# Online Retail Sales Analysis

## Project Overview

This project presents a comprehensive analysis of an online retail dataset using Power BI. The analysis was conducted to support strategic decision-making by identifying sales trends, top-performing markets, and customer behavior. By cleaning and transforming raw data, the project delivers key business insights that help inform market expansion, customer targeting, and seasonal planning strategies.

## Problem Statement

As the company plans strategic expansion, the CEO and CMO require data-driven insights to understand revenue trends, customer behavior, and market opportunities. However, the dataset contains inconsistencies, such as negative quantities and invalid pricing, that must be cleaned before accurate analysis can be performed. This project aims to provide the executive team with clear, actionable insights that support forecasting, customer retention, and global expansion decisions.

## Objective 

1. Clean the dataset by removing invalid entries such as negative quantities, zero or negative prices, and unspecified customer or country values.
1. Analyze monthly revenue trends in 2011 to uncover seasonality and support accurate forecasting.
1. Identify top-performing countries (excluding the United Kingdom) based on revenue and quantity sold.
1. Highlight high-value customers to assist in customer retention and personalized marketing strategies.
1. Evaluate regional product demand to uncover international expansion opportunities.
1. Create interactive, easy-to-understand visuals using Power BI for effective stakeholder communication.

## Dataset Description

The dataset contains transactional records from an online retail store.

1. *InvoiceNo*: Unique identifier for each transaction.
2. *StockCode*: Product/item code.
3. *Description*: Name or description of the product.
4. *Quantity*: Number of items purchased in the transaction.
5. *InvoiceDate*: Date and time when the transaction occurred.
6. *UnitPrice*: Price per individual item.
7. *CustomerID*: Unique identifier for each customer.
8. *Country*: Country where the purchase was made.
9. *Revenue*: Total value of each transaction.

## Skill Demonstrated

### Power Query
- Data Cleaning
- Data Transformation

### Power BI

- Data Visualization
- DAX Functions

## Data Cleaning/Preparation

1. Data Loading & Inspection.

    - Imported the dataset and performed initial structure checks.
  
3. Handling Duplicates.

    -  Removed duplicate entries to ensure data integrity.

4. Handling Inconsistencies.
 
   -  Filtered out invalid quantities and unit prices.

5. Formatting Columns

    - Standardized data types for date, quantity, and pricing fields.

6. Data Validation.

   - Excluded missing or unspecified values to maintain analysis accuracy.

7. Calculated Fields.
   
   - Added a Revenue column (UnitPrice × Quantity) for business insights.

## Exploratory Data Analysis

EDA involved exploring the sales data to answer key questions, such as:

- What is the overall sales trend in 2011?
- Which countries (excluding the UK) drive the most revenue and sales volume?
- Who are our top revenue-generating customers?
- Where is product demand highest outside the UK?

## Data Analysis 
```M language
let
    Source = Excel.Workbook(File.Contents("C:\Users\user\Downloads\Online Retail Data Set (1).xlsx"), null, true),
    #"Online Retail_Sheet" = Source{[Item="Online Retail",Kind="Sheet"]}[Data],
    #"Promoted Headers" = Table.PromoteHeaders(#"Online Retail_Sheet", [PromoteAllScalars=true]),
    #"Changed Type" = Table.TransformColumnTypes(#"Promoted Headers",{{"InvoiceDate", type date}}),
    #"Filtered Rows" = Table.SelectRows(#"Changed Type", each ([UnitPrice] <> 0)),
    #"Changed Type1" = Table.TransformColumnTypes(#"Filtered Rows",{{"UnitPrice", Currency.Type}}),
    #"Filtered Rows1" = Table.SelectRows(#"Changed Type1", each ([Quantity] <> -24 and [Quantity] <> -12 and [Quantity] <> -6 and [Quantity] <> -1)),
    #"Changed Type2" = Table.TransformColumnTypes(#"Filtered Rows1",{{"Quantity", Int64.Type}}),
    #"Removed Duplicates" = Table.Distinct(#"Changed Type2", {"StockCode"}),
    #"Added Custom" = Table.AddColumn(#"Removed Duplicates", "Revenue", each [UnitPrice] * [Quantity]),
    #"Changed Type3" = Table.TransformColumnTypes(#"Added Custom",{{"Revenue", Currency.Type}}),
    #"Filtered Rows2" = Table.SelectRows(#"Changed Type3", each ([Quantity] <> -720 and [Quantity] <> -50 and [Quantity] <> -8 and [Quantity] <> -7 and [Quantity] <> -4 and [Quantity] <> -3 and [Quantity] <> -2))
in
    #"Filtered Rows2"
```
## Business Questions & Insights

1. What are the monthly revenue patterns in 2011, and what seasonal trends can be observed?

   - Revenue peaked in December 2011 at around £168,000, with a strong follow-up in January at £83,000. This shows a clear increase in customer spending during the holiday season.
     
![Revenue Trend](https://github.com/olaide025/Online-Retail-Sales-Analysis-for-Strategic-Business-Expansion/blob/main/Question%201.png)

2. Which countries (excluding the UK) generate the most revenue and quantity sold?
   
   - Ireland (Eire) generated the highest revenue outside the UK, with about £2,098, followed by France at £1,258.
   - Norway sold more items than France but earned less revenue, indicating that customers there likely purchased cheaper products or smaller orders.
   - This shows that higher sales volume doesn’t always translate to higher revenue.

 ![Revenue Trend](https://github.com/olaide025/Online-Retail-Sales-Analysis-for-Strategic-Business-Expansion/blob/main/question%202.png)

3. Who are the top 10 revenue-generating customers?
   - The top 10 customers contributed a large portion of the company’s revenue.
   - The highest spender brought in over $168,000.
   - The lowest contributor among the top 10 generated about $1,000.
   - This wide gap indicates that a small group of loyal customers drives most of the revenue.

 ![Revenue Trend](https://github.com/olaide025/Online-Retail-Sales-Analysis-for-Strategic-Business-Expansion/blob/main/Question%203.png)

4. Which countries show the highest demand for the company’s products, and where should the CEO focus expansion efforts?
   - Ireland (EIRE) clearly stands out as the country with the highest demand, pulling in over 2,280 products.
   - Norway comes next, with just over 1,000 products, followed by France, Germany, and the Netherlands, which round out the top five.
   - Together, these top five countries make up the bulk of international demand, showing where the company’s products are gaining traction.
   
 ![Revenue Trend](https://github.com/olaide025/Online-Retail-Sales-Analysis-for-Strategic-Business-Expansion/blob/main/Question%204.png)

## Recommendation

1. Focus marketing and inventory on Q4 to capitalize on holiday sales.
2. Offer premium products in Norway to boost revenue per sale.
3. Introduce a loyalty program to retain high-value customers.
4. Start expansion with Ireland and Norway—demand is strong.

## About This Project
This project demonstrates my skills in Power BI, Power Query, and data analysis. It highlights my ability to clean and transform messy retail data, uncover key business trends, and deliver insights on customer behavior, regional performance, and revenue patterns.

By building an interactive dashboard, I showcased my data storytelling ability, translating raw numbers into clear, actionable recommendations for business growth and market expansion.

## Power BI File

The complete dashboard file is available for download:

 ![Online Retail Sales Analysis](https://github.com/olaide025/Online-Retail-Sales-Analysis-for-Strategic-Business-Expansion/blob/main/Retail_Performance_Report.pbix)






























