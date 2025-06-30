# DSA-DATA-ANALYST-KMS-PROJECT
Analysis of Kultra Mega Stores (KMS) historical sales, shipping, and customer data (2009-2012) and derive insights to support strategic decisions for the Abuja Division


## 📚 Table of Contents

- [DSA-DATA-ANALYST-KMS-PROJECT](#dsa-data-analyst-kms-project)
- [Detailed Documentation of Each Stage and Analytical Approach Used Throughout the Project Lifecycle](#detailed-documentation-of-each-stage-and-analytical-approach-used-throughout-the-project-lifecycle)
  - [Project Overview](#project-overview)
  - [Exploratory Data Analysis (EDA)](#exploratory-data-analysis-eda)
  - [Purpose of EDA in This KMS Case Study](#purpose-of-eda-in-this-kms-case-study)
  - [EDA Application](#eda-application)
  - [Impact of EDA in This Case Study](#impact-of-eda-in-this-case-study)
- [Step 1: Creation of Database and Data Importation](#step-1-creation-of-database-and-data-importation)
- [Step 2: Data Cleaning](#step-2-data-cleaning)
- [Step 3: Analysis](#step-3-analysis)
  - [Case Scenario I: Operational Performance Analysis](#case-scenario-i-operational-performance-analysis)
    - [Task 1: Which Product Category Had the Highest Sales?](#task-1-which-product-category-had-the-highest-sales)
    - [Task 2: Top 3 and Bottom 3 Regions by Sales](#task-2-top-3-and-bottom-3-regions-by-sales)
    - [Task 3: Total Sales of Appliances in Ontario](#task-3-total-sales-of-appliances-in-ontario)
    - [Task 4: Boosting Revenue from Bottom 10 Customers](#task-4-boosting-revenue-from-bottom-10-customers)
    - [Task 5: Shipping Method with Highest Cost](#task-5-shipping-method-with-highest-cost)
  - [Case Scenario II: Customer Value and Profitability Analysis](#case-scenario-ii-customer-value-and-profitability-analysis)
    - [Task 6: Most Valuable Customers and Purchase Patterns](#task-6-most-valuable-customers-and-purchase-patterns)
    - [Task 7: Top Small Business Customer](#task-7-top-small-business-customer)
    - [Task 8: Most Active Corporate Customer (2009–2012)](#task-8-most-active-corporate-customer-20092012)
    - [Task 9: Most Profitable Consumer Customer](#task-9-most-profitable-consumer-customer)
    - [Task 10: Customers Who Returned Items and Their Segment](#task-10-customers-who-returned-items-and-their-segment)
    - [Task 11: Did KMS Use Shipping Cost Efficiently?](#task-11-did-kms-use-shipping-cost-efficiently)
- [Overall Summary](#overall-summary)


## Detailed Documentation of Each Stage and Analytical Approach Used Throughout the Project Lifecycle

### Project Overview

This project involves a comprehensive SQL-based analysis of historical sales, customer, and shipping data for Kultra Mega Stores (KMS), a leading office supply and furniture retailer having their headquarters located in Lagos, Nigeria. The analysis focuses on supporting strategic decision-making for the Abuja Division using real transactional data from 2009 to 2012.

The goal of this case study is to uncover key insights related to sales performance, customer profitability, logistics efficiency, and regional trends, leveraging SQL Server for data importation, cleaning, transformation, and querying.

The project is divided into two main scenarios:

  - Case Scenario I: Operational Performance which focuses on product categories, regions, shipping costs, and low-performing customers.
  
  - Case Scenario II: Customer Value and Profitability, identifying high-value and returning customers, analyzing segment behavior, and evaluating order priority vs. shipping cost alignment.

Each question in the case study is solved using structured SQL queries, followed by interpretations that include:

  - Actionable insights
  
  - Practical decision tips
  
  -	Strategic business recommendations

This analysis demonstrates how SQL can be used to power data-driven decision-making, improve customer segmentation, reduce operational costs, and strengthen the competitive position of a growing retail organization.

### Exploratory Data Analysis (EDA)

Exploratory Data Analysis (EDA) is the process of examining a dataset to uncover:

  -	Patterns
  
  -	Relationships
  
  -	Anomalies
  
  -	Key trends
  
It involves asking open-ended questions to understand what the data is telling us, before proceeding into complex modeling and/or final decisions.

### Purpose of EDA in This KMS Case Study

In this case study, EDA was essential to:

1.	Understand the structure of the raw data (e.g., column types, missing values, date formats).

2.	Identify key variables relevant to business outcomes:

    -	Sales, Profit, Region, Product Category, Customer Segment, Order Priority, Shipping Cost.
  
3.	Detect inconsistencies or outliers (e.g., negative profits, unusually high shipping costs).
	
4.	Uncover early business questions, such as:

    -	Which products are driving revenue?

    -	Which customers generate the most value?
  
    -	Are expensive shipping methods being used for low-priority orders?

### EDA Application

In this project, EDA was conducted using SQL Server, and included:

  -	Running SELECT and GROUP BY queries to summarize sales and profit by category, region, and segment.

  -	Using COUNT(), SUM(), and ORDER BY to explore distributions.
    
  -	Filtering with WHERE to focus on specific subgroups (e.g., only ‘Small Business’ customers or only ‘Ontario’ province).
    
  -	Identifying potential return activity by detecting negative profits.

### Impact of EDA in This Case Study

EDA helped shape the direction of the analysis by:

  -	Revealing top-performing categories and regions.

  -	Identifying inefficiencies in shipping cost usage.
  
  -	Highlighting customer segments that need targeted strategies.
  
  -	Informing clear business recommendations backed by data.


### Step 1: Creation of Database and Data Importation

Approach:

create database DSA_PROJECT_DB

Used SQL Server Management Studio (SSMS) Import Wizard to load the KMS Sql Case Study.csv file into a table named DBO.[KMS Sql Case Study].

Actions:

-	Right-clicked on the target database → Tasks → Import Flat File.
  
-	Set data types, adjusted column names, and validated data rows.
  
Column,	    Data Type,   	     ✅ Notes

Row_ID,         int,           ✅ Set as Primary Key

Order_ID, 	    int,           	✅

Order_Date, 	  date,	          ✅

Order_Priority, 	nvarchar(50),	✅

Order_Quantity,	  tinyint,	✅ 

Sales,	  decimal(18,2),	✅ 

Discount,  	decimal(18,2),	✅ 

Ship_Mode,	  nvarchar(50),	✅

Profit,	  decimal(18,2),	✅

Unit_Price,  	decimal(18,2),	✅

Shipping_Cost,  	decimal(18,2),	✅

Customer_Name,	  nvarchar(50),	✅

Province,	  nvarchar(50),	✅

Region,	  nvarchar(50),	✅

Customer_Segment,  	nvarchar(50),	✅

Product_Category,	  nvarchar(50),	✅

Product_Sub_Category,	  nvarchar(50),	✅

Product_Name,	  nvarchar(100),	✅ 

Product_Container,	  nvarchar(100),	✅

Product_Base_Margin,	  decimal(18,2),	✅ 

Ship_Date,	  date,	✅


Outcome: 

Clean, structured table with 21 fields (Order ID, Customer Name, Sales, Profit, Order Priority, Ship Mode, etc.).

### Step 2: Data Cleaning

Approach:

Applied SQL data validation techniques to correct column names, check for nulls, and ensure proper data types.

### Key Fixes:

-	Checked for null via this query prompt
  
SELECT 

  COUNT(*) AS Total_Rows,
  
  COUNT(Order_ID) AS Order_ID_NotNull,
  
  COUNT(Customer_Name) AS Customer_Name_NotNull
  
FROM DBO.[KMS Sql Case Study];


-	Checked data type using sql query
  
SELECT 

  COLUMN_NAME, 
  
  DATA_TYPE 
  
FROM INFORMATION_SCHEMA.COLUMNS 

WHERE TABLE_NAME = 'DBO.[KMS Sql Case Study]';


Outcome: Clean and query-ready dataset.


### Step 3: Analysis

### Case Scenario I: Operational Performance Analysis

#### Task 1: Which Product Category Had the Highest Sales?

Approach: Aggregated sales using GROUP BY [Product Category].

SELECT 

    [Product_Category],
    
    SUM(Sales) AS Total_Sales
FROM 

    DBO.[KMS Sql Case Study]
    
GROUP BY 

    [Product_Category]
    
ORDER BY 

    Total_Sales DESC;
    

Insight: Technology was the highest-selling product category.

Decision Tip: Increase inventory and promotions for technology items.

Recommendation: Expand high-performing SKUs; introduce bundles and financing options.


#### Task 2: Top 3 and Bottom 3 Regions by Sales

Approach:

SELECT 

    Region,
    
    SUM(Sales) AS Total_Sales
    
FROM 

    dbo.[KMS Sql Case Study]
    
GROUP BY 

    Region
    
ORDER BY 

    Total_Sales DESC;
    

For Top 3:

	SELECT TOP 3
 
    Region,
    
    SUM(Sales) AS Total_Sales
    
FROM 

    dbo.[KMS Sql Case Study]
    
GROUP BY 

    Region
    
ORDER BY 

    Total_Sales DESC;


For Bottom 3:

SELECT TOP 3

    Region,
    
    SUM(Sales) AS Total_Sales
    
FROM 

    dbo.[KMS Sql Case Study]
    
GROUP BY 

    Region
    
ORDER BY 

    Total_Sales ASC;
    

Insight: Clear regional sales disparity.

Decision Tip: Focus efforts in top regions; investigate bottom regions.

Recommendation: Launch localized marketing in underperforming zones.


#### Task 3: Total Sales of Appliances in Ontario

Approach:

SELECT 

    Province,
    
    [Product_Sub_Category],
    
    SUM(Sales) AS Total_Appliance_Sales
    
FROM 

    dbo.[KMS Sql Case Study]
    
WHERE 

    Province = 'Ontario'
    
    AND [Product_Sub_Category] = 'Appliances'
    
GROUP BY 

    Province, [Product_Sub_Category];
    

Insight: Appliance demand present in Ontario.

Decision Tip: Introduce appliance service warranties or accessories.

Recommendation: Bundle and upsell in high-interest provinces.


#### Task 4: Boosting Revenue from Bottom 10 Customers

Approach: Identified lowest spenders.

SELECT TOP 10

    [Customer_Name],
    
    SUM(Sales) AS Total_Sales
    
FROM 

    dbo.[KMS Sql Case Study]
    
GROUP BY 

    [Customer_Name]
    
ORDER BY 

    Total_Sales ASC;
    

Products bought by the bottom 10 customers

SELECT 

    [Customer_Name],
    
    [Product_Category],
    
    COUNT(*) AS Num_Orders,
    
    SUM(Sales) AS Total_Spent
    
FROM 

    dbo.[KMS Sql Case Study]
    
WHERE 

    [Customer_Name] IN (
    
        SELECT TOP 10 [Customer_Name]
        
        FROM dbo.[KMS Sql Case Study]
        
        GROUP BY [Customer_Name]
        
        ORDER BY SUM(Sales) ASC
        
		)
  
GROUP BY 

    [Customer_Name], [Product_Category]
    
ORDER BY 

    [Customer_Name], Total_Spent DESC;


Insight: Revenue highly concentrated among top customers.

Decision Tip: Create engagement campaigns for low-spenders.

Recommendation: Offer personal discounts and survey feedback loops.


#### Task 5: Shipping Method with Highest Cost

SELECT 

    [Ship_Mode],
    
    SUM([Shipping_Cost]) AS Total_Shipping_Cost
    
FROM 

    dbo.[KMS Sql Case Study]
    
GROUP BY 

    [Ship_Mode]
    
ORDER BY 

    Total_Shipping_Cost DESC;
    

Insight: Express Air was the most expensive shipping method.

Decision Tip: Match shipping mode with order urgency.

Recommendation: Introduce automated shipping prioritization.


### Case Scenario II: Customer Value and Profitability Analysis

#### Task 6: Most Valuable Customers and Purchase Patterns

Approach: Ranked customers by sales, then analyzed category preference.

Top Customers:

SELECT 

    [Customer_Name],
    
    [Customer_Segment],
    
    SUM(Sales) AS Total_Sales
    
FROM 

    dbo.[KMS Sql Case Study]
    
GROUP BY 

    [Customer_Name], [Customer_Segment]
    
ORDER BY 

    Total_Sales DESC;
    

Products or services do they typically purchase:

SELECT 

    [Customer_Name],
    
    [Product_Category],
    
    COUNT(*) AS Num_Orders,
    
    SUM(Sales) AS Category_Sales
    
FROM 

    dbo.[KMS Sql Case Study]
    
WHERE 

    [Customer_Name] IN (
    
        SELECT TOP 10 [Customer_Name]
        
        FROM dbo.[KMS Sql Case Study]
        
        GROUP BY [Customer_Name]
        
        ORDER BY SUM(Sales) DESC
        
    )
    
GROUP BY 

    [Customer_Name], [Product_Category]
    
ORDER BY 

    [Customer_Name], Category_Sales DESC;
    

Insight: Few customers contribute major revenue.

Decision Tip: Prioritize retention for top 10 customers.

Recommendation: Tailor marketing to product preferences.


#### Task 7: Top Small Business Customer

SELECT 

    [Customer_Name],
    
    SUM(Sales) AS Total_Sales
    
FROM 

    dbo.[KMS Sql Case Study]
    
WHERE 

    [Customer_Segment] = 'Small Business'
    
GROUP BY 

    [Customer_Name]
    
ORDER BY 

    Total_Sales DESC;
    

Insight: Strong engagement from top small business.

Decision Tip: Offer Business to Business loyalty plans.

Recommendation: Expand business accounts with similar profiles.


#### Task 8: Most Active Corporate Customer (2009–2012)

Approach: Counted distinct orders per corporate customer.


SELECT 

    [Customer_Name],
    
    COUNT(DISTINCT [Order_ID]) AS Number_Of_Orders
    
FROM 

    dbo.[KMS Sql Case Study]
    
WHERE 

    [Customer_Segment] = 'Corporate'
    
    AND YEAR([Order_Date]) BETWEEN 2009 AND 2012
    
GROUP BY 

    [Customer_Name]
    
ORDER BY 

    Number_Of_Orders DESC;
    

Insight: Corporate client base includes those that make orders frequently.

Decision Tip: Push subscription-based offerings.

Recommendation: Automate re-order and fulfillment workflows.


#### Task 9: Most Profitable Consumer Customer


SELECT 

    [Customer_Name],
    
    SUM(Profit) AS Total_Profit
    
FROM 

    dbo.[KMS Sql Case Study]
    
WHERE 

    [Customer_Segment] = 'Consumer'
    
GROUP BY 

    [Customer_Name]
    
ORDER BY 

    Total_Profit DESC;
    

Insight: High-margin customers exist within consumer segment.

Decision Tip: Model and clone this profile.

Recommendation: Test high-profit product campaigns for similar consumers.


#### Task 10: Customers Who Returned Items and Their Segment

Approach: No return flag so I used negative profits as proxy.


SELECT 

    [Customer_Name],
    
    [Customer_Segment],
    
    COUNT(*) AS Suspected_Returns
    
FROM 

    dbo.[KMS Sql Case Study]
    
WHERE 

    Profit < 0
    
GROUP BY 

    [Customer_Name], [Customer_Segment]
    
ORDER BY 

    Suspected_Returns DESC;
    

Insight: Losses suggest returns.

Decision Tip: Monitor repeat returners.

Recommendation: Tighten return policies and enhance product info.


#### Task 11: Did KMS Use Shipping Cost Efficiently?

Approach: Compare shipping methods used for each Order Priority level and assess if KMS matched priority level to shipping cost/speed.


SELECT 

    [Order_Priority],
    
    [Ship_Mode],
    
    COUNT(*) AS NumOrders,
    
    SUM([Shipping_Cost]) AS Total_Shipping_Cost
    
FROM 

    dbo.[KMS Sql Case Study]
    
GROUP BY 

    [Order_Priority], [Ship_Mode]
    
ORDER BY 

    [Order_Priority], Total_Shipping_Cost DESC;
    

Data Summary:

-	Express Air used across all priorities (even low).

-	Delivery Truck used for some critical orders.
  

Insight: Shipping was not consistently aligned with priority.

Decision Tip: Use fast shipping only for urgent orders.

Recommendation: Implement shipping rules:

Priority	Suggested Shipping

Critical:	Express Air

High:	Regular Air

Medium:	Regular Air

Low:	Delivery Truck

Not Specified:	Delivery Truck

### Overall Summary

KMS can unlock massive efficiency and profitability improvements by:

  -	Prioritizing high-margin categories and regions
    
  -	Segmenting and nurturing high-value customers
    
  -	Enforcing order-priority-based shipping methods
    
  -	Engaging low-spending customers through personalized campaigns
    
    
This case study demonstrates the power of SQL-driven analysis in delivering clear, actionable insights for inventory, logistics, and customer strategy at scale.



