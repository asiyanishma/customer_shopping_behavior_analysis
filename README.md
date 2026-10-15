# Customer Shopping Behavior Analysis

An end-to-end data analytics project that explores customer purchasing behavior using **Python**, **MySQL** and **Power BI**: from cleaning raw data, to answering business questions with SQL, to presenting the results in an interactive dashboard.

!\[Customer Behavior Dashboard](dashboard.png)

## Project Report

The full written project report is available here: [**Customer\_Shopping\_Behavior\_Analysis\_Report.pdf**](Customer_Shopping_Behavior_Analysis_Report.pdf)

## Project Overview

The dataset contains **3,900 customer records across 19 attributes**, covering demographics, purchased items and categories, purchase amounts, review ratings, shipping type, discount usage, subscription status and purchase history.

The goal is to understand who the customers are, what they buy, how discounts, shipping and subscriptions relate to spending, and which customer groups drive revenue.

## Tools and Technologies

|Tool|Used for|
|-|-|
|Python (Pandas, NumPy, Matplotlib, Seaborn)|Data exploration, cleaning and feature engineering|
|Jupyter Notebook|Interactive analysis|
|SQLAlchemy + PyMySQL|Loading the cleaned data into MySQL|
|MySQL|Business-question analysis with SQL|
|Power BI|Interactive dashboard|
|Git and GitHub|Version control|

## Workflow

### 1\. Data exploration and cleaning (Python)

* Loaded the dataset with Pandas and inspected its structure with `info()`, `describe()` and `isnull()`.
* Checked for missing values and duplicate records (`isnull()` and `duplicated()`).
* Filled missing **review ratings** using the **median rating of each product category**.
* Standardized column names (lowercase, underscores) and renamed the purchase amount column.
* Confirmed that `promo\_code\_used` matched `discount\_applied` exactly, then dropped it as redundant.

### 2\. Feature engineering

* **`age\_group`**: customers split into four quartile-based groups (Young Adult, Adult, Middle-Aged, Senior).
* **`purchase\_frequency\_days`**: purchase frequency labels (Weekly, Monthly, Quarterly, etc.) converted into a number of days.

### 3\. SQL analysis (MySQL)

The cleaned data was loaded into a MySQL table named `customer`. The queries in [`customer\_shopping\_behavior.sql`](customer_shopping_behavior.sql) use aggregations, subqueries, CTEs, `CASE` statements and window functions (`ROW\_NUMBER`) to answer 10 questions:

1. Total revenue from male vs. female customers
2. Customers who used a discount but still spent more than the average purchase amount
3. Top 5 products by average review rating
4. Average purchase amount: Standard vs. Express shipping
5. Do subscribers spend more? (average spend and total revenue)
6. Top 5 products by share of purchases made with a discount
7. Customer segments: New, Returning and Loyal
8. Top 3 most purchased products within each category
9. Are repeat buyers (more than 5 purchases) more likely to subscribe?
10. Revenue contribution of each age group

### 4\. Dashboard (Power BI)

An interactive dashboard with:

* **KPI cards:** number of customers, average review rating, average purchase amount
* **Charts:** subscription split, revenue and sales by category, revenue and sales by age group
* **Slicers:** subscription status, gender, category and shipping type

## Key Findings

* **Clothing is the top category** for both revenue and sales: about **$104K, roughly 45% of total revenue**, followed by Accessories, Footwear and Outerwear.
* Only **about 27% of customers are subscribers**, and about 73% are not, which leaves room to grow subscriptions.
* **Young Adults generate the most revenue**, although the gap to the other age groups is small.
* Across all customers, the **average review rating is 3.75** and the **average purchase amount is $59.76**.

## Project Structure

```
customer\_shopping\_behavior\_analysis/
│
├── customer\_shopping\_analysis.ipynb      # Python cleaning, EDA and feature engineering
├── customer\_shopping\_behavior.sql        # MySQL queries
├── customer\_behavior\_dashboard.pbix      # Power BI dashboard
├── customer\_behavior\_dashboard.pdf       # PDF export of the dashboard
├── Customer\_Shopping\_Behavior\_Analysis\_Report.pdf  # Project report
├── dashboard.png                         # Dashboard preview
├── data/
│   └── customer\_shopping\_behavior.csv    # Dataset
├── LICENSE
└── README.md
```

## How to Run

**Requirements:** Python 3, Jupyter Notebook, MySQL Server with MySQL Workbench, and Power BI Desktop.

1. **Clone the repository**

```bash
   git clone https://github.com/asiyanishma/customer\_shopping\_behavior\_analysis.git
   cd customer\_shopping\_behavior\_analysis
   ```

2. **Install the Python libraries**

```bash
   pip install pandas numpy matplotlib seaborn sqlalchemy pymysql notebook
   ```

3. **Create the database** in MySQL Workbench:

```sql
   CREATE DATABASE customer\_behavior;
   ```

4. **Run the notebook.** Open `customer\_shopping\_analysis.ipynb` and run the cells in order. The connection cell asks for your MySQL password when you run it, so no password is stored in the file. The last cells write the cleaned data to a MySQL table named `customer`.
5. **Run the SQL.** Open `customer\_shopping\_behavior.sql` in MySQL Workbench, select the `customer\_behavior` database, and run the queries.

**Open the dashboard.** Open `customer\_behavior\_dashboard.pbix` in Power BI Desktop. If asked, update the data source path and refresh.



Future Improvements

* Add more detailed customer segmentation (for example, RFM analysis).
* Analyze subscription conversion among repeat buyers in more depth.
* Add more dashboard pages and drill-through filters.
* Automate the data preparation and reporting steps.

## Author

**Asiya Nishma**
GitHub: [asiyanishma](https://github.com/asiyanishma)

