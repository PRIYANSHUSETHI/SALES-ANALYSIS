# Sales Analysis Using Python

## Overview
This project performs an exploratory sales analysis using Python. The dataset consists of monthly sales data from 2019. The analysis aims to provide insights into sales trends, best-performing products, and optimal advertising times to maximize revenue.

## Dataset
The project uses multiple CSV files, each representing monthly sales data for the year 2019. The files are merged into a single DataFrame for analysis.

## Libraries Used
- **`pandas`** – For data manipulation and preprocessing
- **`matplotlib.pyplot`** – For visualizing sales trends
- **`collections.Counter`** – For analyzing product pairings
- **`itertools.combinations`** – For identifying commonly purchased product pairs

## Project Workflow
### 1. Data Loading and Cleaning
- **Merging multiple CSV files** into a single DataFrame using `pd.concat()`.
- **Handling missing values** using `dropna()`.
- **Converting `Order Date` column to datetime format** using `pd.to_datetime()`.
- **Extracting the Month** from `Order Date` using `.dt.month`.
- **Ensuring numeric data types** for `Quantity Ordered` and `Price Each` using `pd.to_numeric()`.
- **Calculating total sales** by multiplying `Quantity Ordered` and `Price Each`.

### 2. Sales Analysis
#### **Q1: What was the best month for sales?**
- **Grouping data by month** using `.groupby('Month')[['Sales']].sum()`.
- **Visualizing sales performance** using `plt.bar()`.
- **Result**: December had the highest sales (~4.61 million).

#### **Q2: Which city had the highest sales?**
- **Extracting city names** from the `Purchase Address` column using `.str.split(',')`.
- **Grouping and sorting sales by city** using `.groupby('Purchase City')[['Sales']].sum()`.
- **Visualizing sales by city** using `plt.bar()`.
- **Result**: San Francisco had the highest sales (~8.26 million).

#### **Q3: What time should advertisements be placed to maximize sales?**
- **Extracting hour** from `Order Date` using `.dt.hour`.
- **Counting orders per hour** using `.groupby('Hour')[['Order ID']].count()`.
- **Visualizing orders by hour** using `plt.bar()`.
- **Result**: The best hours for advertising are **10 AM – 1 PM and 6 PM – 8 PM**.

#### **Q4: What products are often sold together?**
- **Identifying duplicate `Order ID`s** to find multiple purchases.
- **Using `groupby('Order ID')` and `transform(lambda x: ','.join(x))`** to list product combinations.
- **Counting frequent product pairs** using `Counter(combinations(row_list, 2))`.
- **Result**: **iPhone & Lightning Charging Cable** is the most common product pair.

#### **Q5: What is the most sold product?**
- **Grouping by product** and summing `Quantity Ordered`.
- **Sorting products by sales volume** using `.sort_values('Quantity Ordered', ascending=False)`.
- **Visualizing product sales** using `plt.bar()`.
- **Result**: **AAA Batteries (4-Pack)** is the most purchased product.

## How to Run the Project
1. Install the required libraries:
   ```bash
   pip install pandas matplotlib
   ```
2. Place the monthly sales CSV files in the same directory as the script.
3. Run the Python script or Jupyter Notebook.
4. Analyze the generated charts and insights.

## Future Improvements
- Include **price trends** to analyze revenue impact.
- Perform **customer segmentation** for targeted marketing.
- Apply **machine learning models** for demand forecasting.

## Conclusion
This project provides data-driven insights into sales trends, customer behavior, and product performance. Businesses can use these findings to optimize inventory, marketing strategies, and sales forecasting.
