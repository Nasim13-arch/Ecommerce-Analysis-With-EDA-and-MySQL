# Ecommerce Analysis With EDA and MySQL

# Overview
This project analyzes Brazilian e-commerce data to uncover trends in monthly revenue growth, order volume, and product performance. The dataset is sourced from [Kaggle: Brazilian E-Commerce Dataset](https://www.kaggle.com/datasets/olistbr/brazilian-ecommerce) and processed using MySQL before analysis in Python.

# Files in the Project
    1. Revenue Trends.csv

        Contains monthly revenue and order count data.

        Extracted using a MySQL query (see below).

    2. Top Sell Item.csv

        Contains product-wise sales and revenue data.

        Extracted using a MySQL query (see below).

# SQL Queries Used to Extract Data
    The CSV files were generated by running the following MySQL queries on the Brazilian E-Commerce Dataset:

    1. Monthly Revenue & Order Count (Revenue Trends.csv)

    SELECT DATE_FORMAT(o.order_purchase_timestamp, '%Y-%m') AS month,
    SUM(oi.price) AS revenue,
    COUNT(DISTINCT o.order_id) AS orders_count
    FROM orders o
    JOIN order_items oi ON o.order_id = oi.order_id
    GROUP BY month
    ORDER BY month;

    2. Top Selling Products (Top Sell Item.csv)

    SELECT p.product_id,
    p.product_category_name,
    SUM(oi.price) AS total_revenue,
    COUNT(oi.order_item_id) AS items_sold
    FROM products p
    JOIN order_items oi ON p.product_id = oi.product_id
    GROUP BY p.product_id, p.product_category_name
    ORDER BY total_revenue DESC;

# Analysis & Visualizations
    1. Monthly Revenue Growth
    A line chart showing revenue trends over time.

    Helps identify seasonal patterns and growth trends.

    2. Revenue vs. Order Volume
    A dual-axis plot comparing revenue and order count.

    Reveals whether higher revenue is driven by more orders or higher-value purchases.

    3. Product Performance: Revenue vs. Units Sold
    A scatter plot highlighting top-performing products.

    Size and color represent revenue, helping identify high-impact products.

    4. Top 5 Products by Revenue
    A bar chart showing the highest-revenue products.

    A box plot displaying revenue distribution across all products.

# Technologies Used
    Python (Pandas, Matplotlib, Seaborn)

    MySQL (Data Extraction)

    Jupyter Notebook / VS Code (Analysis)

# How to Run the Code
    1. Install dependencies: pip install pandas matplotlib seaborn

    2. Download the dataset from Kaggle.

    3. Run the SQL queries to generate the required CSV files.

    4. Update the file paths in the Python script to match your local directory.

    5. Execute the script to generate visualizations.

# Key Insights
    Revenue trends (growing/declining months).

    Order-to-revenue relationship (are more orders driving revenue?).

    Best-selling products (which items contribute most to revenue?).





