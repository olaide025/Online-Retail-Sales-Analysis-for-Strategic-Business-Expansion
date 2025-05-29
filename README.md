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

## Data Cleaning and Preparation

To ensure accurate and reliable analysis, several data preprocessing steps were carried out using Power Query in Power BI:

1. Invoice Date:
   - Converted the InvoiceDate column to the Date data type to support accurate time-based aggregation and trend analysis.

2. Unit Price:
   - Removed rows where UnitPrice was zero or negative, as such values indicate invalid transactions.
   - Converted the column to Fixed Decimal Number to preserve numeric precision during calculations.

3. Quantity:
   - Excluded records with Quantity less than 1, including negative values that represent product returns.
   - Updated the data type to Whole Number for consistency and calculation accuracy.

4. Duplicates:
   - Removed all duplicate records

5. Revenue Column:
   - Created a new Revenue column by multiplying UnitPrice by Quantity, providing a measure of total sales value for each transaction.

6. Country:
   - Removed a single record labeled as "Unspecified" in the Country field to maintain geographic consistency in the analysis.

7. Customer ID:
   - Approximately 31% of entries in the CustomerID column were missing. These rows were filtered out to ensure the integrity of customer-level analysis, particularly for Question 3, which focuses on identifying the top 10 customers by revenue.













