# Data Analysis Project: Amazon Reviews & KMS Inventory views

 Welcome to my data analysis project repository! This project combines two case studies to showcase the use of **SQL**, **Excel**, **Pivot Tables**, and **Dashboard Design** to derive practicable business insights from raw data.

 ## Project Overview

 This project includes two case studies:
 
1. **Amazon Product Review Analysis**  
2. **Kultra Mega Stores (KMS) Inventory Analysis**

Both case studies are designed to demonstrate my skills in:
- Data cleaning
- Exploratory data analysis
- Business intelligence
- Dashboard creation
- SQL querying and reporting

## 📊 Case Study 1: Amazon Product Review Analysis

**Synopsis**:  
As a Junior Data Analyst at *RetailTech Insights*, I was tasked with analyzing Amazon product and customer review data to uncover trends, consumer behavior, and product performance metrics.

**Objectives**:
- Calculate average discounts and ratings
- Identify high-performing products
- Analyze customer engagement through reviews
- Explore pricing buckets and potential revenue
- Determine how rating relates to discount level

**Tools Used**:  
- Excel (Pivot Tables, Formulas, Charts)
- Basic statistical analysis

---

## 🏬 Case Study 2: Kultra Mega Stores (KMS) Inventory Analysis

**Synopsis**:  
As a Business Intelligence Analyst at *KMS* (a Nigerian retail and wholesale store), I analyzed historical order data (2009–2012) to support the Abuja division with performance insights and strategic recommendations.

**Objectives**:
- Determine top-performing product categories and regions
- Analyze small business and corporate customer behavior
- Identify the most profitable and most returning customers
- Evaluate shipping method cost-effectiveness based on order priority
- Recommend ways to increase revenue from bottom-tier customers

**Tools Used**:
- SQL (for querying and aggregation)
- Excel (for visualization and reporting)
- Logical reasoning for business recommendations

---

##  Folder Structure

Data-Analysis-Project/

Case_Study_1_Amazon_Product_Review/
│   ├── 📄 Amazon_Review_Data.xlsx
│   ├── 📄 Amazon_Review_Analysis.md
│   ├── 📄 Dashboard_Screenshot_Amazon.png
│   └── 📄 

Case_Study_2_KMS_Inventory_Analysis/
│   ├── 📄 KMS_Inventory_Data.xlsx
│   ├── 📄 KMS_Case_Study_Answers.md
│   ├── 📄 SQL_Queries_KMS.sql
│   ├── 📄 Dashboard_Screenshot_KMS.png
│   └── 📄 
│
├── 📄 README.md  ← Project overview and instruction

 

NOTE: Please I was unable to upload my files.



KMS_Inventory_Data.xlsx

select *
from [KMS Sql Case Study1]


--- Which product category that has the highest 

select top 1 [Product_Category],count ([Product_Category])as [Product Count]
from [KMS Sql Case Study1]
group by Product_Category
order by [Product Count] desc


--- what are the top 3 and buttom 3 region in terms of sales 

select top 3 [Region],sum([sales]) as [Total Sales]
from [KMS Sql Case Study1]
group by Region
order by [Total Sales] desc

select top 3 [Region],sum([sales]) as [Total Sales]
from [KMS Sql Case Study1]
group by Region
order by [Total Sales] asc

----- what were  the Total Sales of applicants in ontario?

select Region, SUM(sales) as [Total Sales]
from [KMS Sql Case Study1]
where Region='ontario'
Group by Region

--------Advice the management of KMS on what to do to increase the revenue from the buttom 10 customer 

Select top 10 [Customer_Name], SUM([Sales]) as [Total Sales]
from [KMS Sql Case Study1]
group by Customer_Name
order by [Total Sales] asc

------KMS incurred the Most shipping cost using which shipping method ?

Select Top 1 [Ship_Mode], SUM([Shipping_Cost]) as [Total Shipping Cost]
from [KMS Sql Case Study1]
group by Ship_Mode
order by [Total Shipping Cost] desc

----Who are the most valuable customer, and what products or services did they typically purchase?

select [Customer_Name],Product_Name, SUM(sales) as [Total Sales]
from [KMS Sql Case Study1]
Group by Customer_Name,Product_Name
order by [Total Sales] desc

-----Which small business customer have the highest sales ?

select top 1 Customer_Name,Customer_Segment, SUM([Sales]) as [Total Sales]
from [KMS Sql Case Study1]
where Customer_Segment ='small Business'
group by Customer_Name,Customer_Segment
order by [Total Sales] desc

---Which corporate customer placed the most number of orders in 2019 -2012?

select top 1  Customer_Name,Customer_Segment, count([Order_ID]) as [Total order]
from [KMS Sql Case Study1]
where Customer_Segment ='corporate' and Order_Date between '2009' and '2012'
group by Customer_Name,Customer_Segment
order by [Total order] desc

---  Which consumer customer was the most profitable one?

select top 1 Customer_Name,Customer_Segment, sum([Profit]) as [Total profit]
from [KMS Sql Case Study1]
where Customer_Segment ='Consumer'
group by Customer_Name,Customer_Segment
order by [Total profit] desc

----Which customer returned items, and what segments do they belong to?
select Customer_Name,Customer_Segment,[Status]
from [KMS Sql Case Study1]
join [dbo].[Order_Status]
on [KMS Sql Case Study1].Order_ID = [dbo].[Order_Status].[Order_ID]

/* If the delivery truck is the most economical but the lowest shipping method and express air is the fastest.
but the most expensive one, did you think the company appropriately spent shipping costs based on the order priority */

Select Order_Priority, Ship_Mode,
    COUNT([Order_ID]) AS [order count],
    SUM(sales - profit) AS [Estimated shipping cost],
    AVG(DATEDIFF(DAY, [Order_Date], [Ship_Date])) AS [Avg ship date]
from  [KMS Sql Case Study1] 
group by Order_Priority,Ship_Mode
order by  Order_Priority,Ship_Mode desc       
     
/* No, KMS did not appropriately spend shipping costs based on the order of  priority.
They overused delivery trucks, which are best for bulk or non-urgent orders and 
underused express air, which is meant for urgent deliveries. 
This shows a misalignment between shipping cost,speed and order priority leading to inefficient spending and wasted cost .*/


select Customer_Segment, SUM(sales) as [total sales]
from [KMS Sql Case Study1]
group by Customer_Segment
order by [total sales] desc





select *
from [KMS Sql Case Study1]


--- Which product category that has the highest 

select top 1 [Product_Category],count ([Product_Category])as [Product Count]
from [KMS Sql Case Study1]
group by Product_Category
order by [Product Count] desc


--- what are the top 3 and buttom 3 region in terms of sales 

select top 3 [Region],sum([sales]) as [Total Sales]
from [KMS Sql Case Study1]
group by Region
order by [Total Sales] desc

select top 3 [Region],sum([sales]) as [Total Sales]
from [KMS Sql Case Study1]
group by Region
order by [Total Sales] asc

----- what were  the Total Sales of applicants in ontario?

select Region, SUM(sales) as [Total Sales]
from [KMS Sql Case Study1]
where Region='ontario'
Group by Region

--------Advice the management of KMS on what to do to increase the revenue from the buttom 10 customer 

Select top 10 [Customer_Name], SUM([Sales]) as [Total Sales]
from [KMS Sql Case Study1]
group by Customer_Name
order by [Total Sales] asc
/* To boost sales from the bottom 10 customers, the company should focus on strengthening relationships 
through customized promotions, puchasing behaviours, Reaching out directly through calls or emails to their customers to understand their past experience,
Give discounts on their most viewed or previously purchased products, Upsell and Cross-sell Offers,
Offer faster delivery, better after-sales support, or dedicated account managers for small businesses and  Survey to Understand 
the Needs of the customers, what would make them again and why they havent been coming frequently*/

------KMS incurred the Most shipping cost using which shipping method ?

Select Top 1 [Ship_Mode], SUM([Shipping_Cost]) as [Total Shipping Cost]
from [KMS Sql Case Study1]
group by Ship_Mode
order by [Total Shipping Cost] desc

----Who are the most valuable customer, and what products or services did they typically purchase?

select [Customer_Name],Product_Name, SUM(sales) as [Total Sales]
from [KMS Sql Case Study1]
Group by Customer_Name,Product_Name
order by [Total Sales] desc

-----Which small business customer have the highest sales ?

select top 1 Customer_Name,Customer_Segment, SUM([Sales]) as [Total Sales]
from [KMS Sql Case Study1]
where Customer_Segment ='small Business'
group by Customer_Name,Customer_Segment
order by [Total Sales] desc

---Which corporate customer placed the most number of orders in 2019 -2012?

select top 1  Customer_Name,Customer_Segment, count([Order_ID]) as [Total order]
from [KMS Sql Case Study1]
where Customer_Segment ='corporate' and Order_Date between '2009' and '2012'
group by Customer_Name,Customer_Segment
order by [Total order] desc

---  Which consumer customer was the most profitable one?

select top 1 Customer_Name,Customer_Segment, sum([Profit]) as [Total profit]
from [KMS Sql Case Study1]
where Customer_Segment ='Consumer'
group by Customer_Name,Customer_Segment
order by [Total profit] desc

----Which customer returned items, and what segments do they belong to?
select Customer_Name,Customer_Segment,[Status]
from [KMS Sql Case Study1]
join [dbo].[Order_Status]
on [KMS Sql Case Study1].Order_ID = [dbo].[Order_Status].[Order_ID]

/* If the delivery truck is the most economical but the lowest shipping method and express air is the fastest.
but the most expensive one, did you think the company appropriately spent shipping costs based on the order priority */

Select Order_Priority, Ship_Mode,
    COUNT([Order_ID]) AS [order count],
    SUM(sales - profit) AS [Estimated shipping cost],
    AVG(DATEDIFF(DAY, [Order_Date], [Ship_Date])) AS [Avg ship date]
from  [KMS Sql Case Study1] 
group by Order_Priority,Ship_Mode
order by  Order_Priority,Ship_Mode desc

