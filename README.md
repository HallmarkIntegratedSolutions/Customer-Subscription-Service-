# Customer Subscription Service

## Project Aim
This project involves analyzing customer data for a subscription service to identify 
segments and trends. The goal is to understand customer behavior, track subscription types, 
and identify key trends in cancellations and renewals.

-----------

## Tools Used
1. Microsoft EXCEL for Data Cleaning, Data Summarization and Data Analysis
2. SQL for Data Analysis
3. Power BI for Data Cleaning, Data Transformation and Data Visualization
4. GitHub for Report Documentation
----------

## Data Summarization with MS EXCEL

Customer data was summarized using pivot tables to find subscription patterns.

#### Summarization of total subscription revenue per region

![Sub 1 1~2](https://github.com/user-attachments/assets/e9bddd03-88a1-404e-ac88-e009ea407f63)

*fig 1: Total revenue per region*

The region with the highest subscription revenue is East with 16,958,763 while the region with the lowest subscription revenue is North with 16,817,972. 

---------

#### Summarization of frequency (count) of customers by their subscription type

![Sub 1 2~2](https://github.com/user-attachments/assets/22ab5819-50da-4c98-9cab-a4dfd01cebbc)

*fig 2: Frequency by Subscription Type*

The most popular subscription type is Basic with 16,921 customers while the subscription type with the least customers is Standard with 8,420 customers. 

----------

#### Summarization of frequency (count) of customers by their subscription cancellation

![Sub 1 3~2](https://github.com/user-attachments/assets/c6c2ebc0-b27f-4b1a-ad31-8046d2ac4068)

*fig 3: Frequency by Subscription Cancellation*

Most of the customers (18,612) cancelled their subscription while 15,175 customers did not cancel their subscription


#### Summarization of total subscription revenue per subscription type

![Sub 1 4~2](https://github.com/user-attachments/assets/48d88736-75e3-4a7f-ab9f-a32d6ba30ba3)

*fig 4: Total revenue by Subscription Type*

Basic subscription type returned the highest revenue of 33,776,735 while standard subscription type returned the lowest revenue of 16,864,376.

------------

## Data Analysis with MS EXCEL

- Average Subscription Duration
To calculate the average subscription duration, each customer subscription duration was calculated in a new column with the formula:

```MICROSOFT EXCEL
=F2-E2
```

Then the average of the subscription duration for all customers was calculated with the formula:

```MICROSOFT EXCEL
=AVERAGE(I2:I33788)
```

The average subscription duration is 365 days.

---------------


## Data Analysis with SQL

- To calculate the total number of customers from each region

```SQL
select region, count(CustomerID) as Total_Number_of_Customers
from [dbo].[CustomerSubscription]
group by region
order by 2 desc
```
![Sub 1 5~2](https://github.com/user-attachments/assets/c129ca4c-be94-4fb5-9349-7c9cf84f3b84)


The region with the highest frequency of customers is East with 8,488 customers while West had the lowest frequency of customers with 8,420 customers. 

------------

- To calculate most popular subscription type by the number of customers
```SQL
select top 1 SubscriptionType, count(customerID) as Total_Number_of_Customers
from [dbo].[CustomerSubscription]
group by SubscriptionType
```



The most popular subscription type by number of customers is Basic with 16,921 subscriptions. 



