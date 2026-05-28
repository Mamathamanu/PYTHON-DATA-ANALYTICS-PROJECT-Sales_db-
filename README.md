# PYTHON-DATA-ANALYTICS-PROJECT-Sales_db
🔹 STEP 1: Open Python Environment
You can use:
•	Jupyter Notebook
•	Google Colab
•	VS Code (Jupyter extension)

Python is a high-level programming language widely used for data analysis, visualization, and automation.
________________________________________
🔹 STEP 2: Import Required Libraries
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns
📌 Why these libraries?
•	pandas → data handling
•	matplotlib → plotting
•	seaborn → advanced visualization

Pandas is used for data manipulation, Matplotlib and Seaborn are used for data visualization in Python.
________________________________________
🔹 STEP 3: Load the Dataset
df = pd.read_excel("Beginner_Sales_Data.xlsx")
Check data:
df.head()

The dataset is loaded using pandas read_excel() function which converts Excel data into a DataFrame.
________________________________________
🔹 STEP 4: Understand the Dataset
df.info()
df.describe()
What this shows:
•	Columns & data types
•	Null values
•	Statistical summary

The info() function provides column details and data types, while describe() gives statistical summary like mean, min, max, and count.
________________________________________
🔹 STEP 5: Data Cleaning
Check missing values
df.isnull().sum()
Remove missing values
df = df.dropna()

Data cleaning removes missing and inconsistent data to improve analysis accuracy.
________________________________________
🔹 STEP 6: KPI Calculations (MOST IMPORTANT)
✅ Total Sales
total_sales = df['Sales'].sum()
total_sales
✅ Total Profit
total_profit = df['Profit'].sum()
total_profit
✅ Total Quantity
total_quantity = df['Quantity'].sum()
total_quantity
✅ Average Sales
average_sales = df['Sales'].mean()
average_sales

KPI calculations help measure business performance. In this project, total sales, profit, quantity, and average sales were calculated using pandas aggregation functions.
________________________________________
🔹 STEP 7: Category-wise Sales (Bar Chart)
category_sales = df.groupby('Category')['Sales'].sum()

category_sales.plot(kind='bar')
plt.title("Category-wise Sales")
plt.xlabel("Category")
plt.ylabel("Sales")
plt.show()
📌 Insight Example
Technology category has the highest sales.

Bar charts are used to compare sales across categories.
________________________________________
🔹 STEP 8: Sales Trend Over Time (Line Chart)
df['Order Date'] = pd.to_datetime(df['Order Date'])
date_sales = df.groupby(df['Order Date'].dt.year)['Sales'].sum()

date_sales.plot(kind='line')
plt.title("Year-wise Sales Trend")
plt.xlabel("Year")
plt.ylabel("Sales")
plt.show()

Line charts are used to analyze trends and patterns in sales over time.
________________________________________
🔹 STEP 9: Region-wise Sales (Pie Chart)
region_sales = df.groupby('Region')['Sales'].sum()

region_sales.plot(kind='pie', autopct='%1.1f%%')
plt.title("Region-wise Sales Distribution")
plt.ylabel("")
plt.show()

Pie charts show percentage contribution of regions to total sales.
<img width="729" height="655" alt="Screenshot 2026-05-28 234836" src="https://github.com/user-attachments/assets/91b5bad1-88da-49a9-a87e-64b5035eab53" />
<img width="587" height="495" alt="Screenshot 2026-05-28 234857" src="https://github.com/user-attachments/assets/e823b476-4e4c-4dbd-b898-c9437fe59884" />
<img width="845" height="614" alt="Screenshot 2026-05-28 234913" src="https://github.com/user-attachments/assets/2a1f2036-0a63-4c08-82fb-3c6ec7c6c66b" />

________________________________________
🔹 STEP 10: Top 10 Customers by Sales
top_customers = df.groupby('Customer Name')['Sales'].sum().sort_values(ascending=False).head(10)
top_customers

Top-N analysis identifies high-value customers contributing most to revenue.
Customer_ID
1058    111536.20
1090    111490.35
Name: Sales_Amount, dtype: float64
Customer_ID
1007     914.4
1014    1621.8
Name: Sales_Amount, dtype: float64
