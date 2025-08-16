# Sales-dashboard

##  Project Overview
This project is an **interactive Sales Dashboard** built using **Power BI** with **MySQL** as the data source.  
It provides insights into revenue, sales quantity, profit margin, and performance across different regions and time periods.  

The goal of this dashboard is to help business stakeholders track key sales metrics and identify trends for better decision-making.

## Tools & Tech Stack
•	📊 Power BI Desktop → Main data visualization platform used for dashboard creation

•	🧹 Power Query → Data transformation & cleaning layer for reshaping and preparing data

•	📐 DAX (Data Analysis Expressions) → Used for calculated measures & KPIs

•	🗄️ MySQL → Data storage, queries, and validation

•	🔗 Data Modeling → Relationships established among the tables	

##  Dataset
- **Source**: MySQL dump file (provided as part of a learning project)  
- **Contents**:  
  - `sales. Customers` → customer details (customer name, customer code, customer type)  
  - `sales. Date` → (year,month,name)
  - `sales. Markets` → Market details (market code, market name, and zone)  
  - `sales. Products` → product details (product code, product type)
  - `sales. Transactions` → Sales data (product code,customer code,market code,order date,sales quantity,sales amount,currency,profit margin percentage,profit margin, cost price)  


## Data Cleaning & Transformation
Data preparation was performed in **Power Query**:
- Most of the dataset was clean.  
- **Removed rows**:  
  - 2 markets (`New York` and `Paris`) → No `zone` assigned and not part of Indian market dataset.  
- **Standardization**: Indian markets were categorized into zones (`North`, `Central`, `South`).  
- Final dataset was consistent and ready for analysis.  


## Measures Created in Power BI (DAX)
To perform business analysis, I created the following measures:
- **Revenue**  
- **sales Qnatity**
- **Revenue contribution %**
- **Profit margin %**
- **Profit margin contribution %**

These measures help understand sales performance, profitability, and contribution of each market/zone.
## Data Analysis in MySQL
Before and during dashboard development, I used SQL queries to analyze data and validate dashboard results.
Examples of analysis:
```sql

1] select sum(transactions.sales_amount)
from transactions;

2] select sum(sales.transactions.sales_amount)
from sales.transactions
inner join sales.date
on 
sales.transactions.order_date=sales.date.date
where sales.date.year=2020
and sales.transactions.market_code="Mark001";

3] select distinct product_code
from sales.transactions
where market_code="Mark001";

4] select sum(sales.transactions.sales_qty) as total_sales_qty
from sales.transactions 
inner join sales.date
on
sales.transactions.order_date=sales.date.date
where date.year='2020';

etc,,,

## Features

- **KPI Cards** → Total Revenue & Sales Quantity  
- **Filters/Slicers** → Year & Month selection  
- **Revenue by Markets** → Contribution of each city/region  
- **Profit Contribution % by Market** → Comparison of profit across regions  
- **Profit Margin % by Market** → Margin analysis  
- **Revenue Trend** → Revenue by Year, Quarter, and Month  
- **Profit Margin Contribution by Zone** → Regional distribution of margins  

## Key Insights from Dashboard:
•	Delhi NCR contributes 52% of total revenue and 48% of total profit.
•	Mumbai and Ahmedabad are the next major contributors to revenue.
•	Surat and Patna show the highest profit margins among markets.
•	Overall revenue trend shows seasonal fluctuations between 2018–2020.
•	North Zone contributes the majority of profit margin (61%).

## 📊 Dashboard Preview
![Dashboard Overview](https://github.com/umashree2803/Sales-dashboard/blob/main/Dashboard%20screenshot.png)


## Conclusion
This project helped me gain hands-on experience in end-to-end data analysis:
1.	Importing and cleaning raw data
2.	Analyzing data in MySQL
3.	Designing a data model in Power BI
4.	Creating insightful measures with DAX
5.	Validating results with SQL
6.	Building a professional business dashboard in Power BI



