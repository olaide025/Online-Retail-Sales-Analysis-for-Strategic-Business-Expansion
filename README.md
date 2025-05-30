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

   - Revenue peaked in **December**, with significant activity also in **January**, suggesting strong seasonal demand around the **holiday period**. These trends provide a basis for 
     forecasting and planning inventory or marketing campaigns for future peak seasons
     
![Revenue Trend](https://github.com/olaide025/Online-Retail-Sales-Analysis-for-Strategic-Business-Expansion/blob/main/Question%201.png)

2. Which countries (excluding the UK) generate the most revenue and quantity sold?
   
   - The Netherlands, Ireland, and Germany emerged as top-performing countries in terms of both revenue and sales volume. These regions show strong potential for targeted marketing and 
     operational focus.

   ![Revenue Trend](https://github.com/olaide025/Online-Retail-Sales-Analysis-for-Strategic-Business-Expansion/blob/main/Question%202.png)





























