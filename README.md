# Project Title: Customer Subscription Service


[Project Aim](#Project-Aim)

[Tools Used](#Tools-Used)

[Data Summarization with EXCEL](#Data-Summarization-with-EXCEL)

[Data Analysis with EXCEL](#Data-Analysis-with-EXCEL)

[Data Analysis with SQL](#Data-Analysis-with-SQL)

[Data Visualization with POWER BI](#Data-Visualization-with-POWER-BI)

[Conclusion](#Conclusion)


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

## Data Summarization with EXCEL

Customer data was summarized using pivot tables to find subscription patterns.

#### Summarization of total subscription revenue per region

![Sub 1 1~2](https://github.com/user-attachments/assets/e9bddd03-88a1-404e-ac88-e009ea407f63)

The region with the highest subscription revenue is East with 16,958,763 while the region with the lowest subscription revenue is North with 16,817,972. 

---------

#### Summarization of frequency (count) of customers by their subscription type

![Sub 1 2~2](https://github.com/user-attachments/assets/22ab5819-50da-4c98-9cab-a4dfd01cebbc)

The most popular subscription type is Basic with 16,921 customers while the subscription type with the least customers is Standard with 8,420 customers. 

----------

#### Summarization of frequency (count) of customers by their subscription cancellation

![Sub 1 3~2](https://github.com/user-attachments/assets/c6c2ebc0-b27f-4b1a-ad31-8046d2ac4068)

Most of the customers (18,612) cancelled their subscription while 15,175 customers did not cancel their subscription


#### Summarization of total subscription revenue per subscription type

![Sub 1 4~2](https://github.com/user-attachments/assets/48d88736-75e3-4a7f-ab9f-a32d6ba30ba3)

Basic subscription type returned the highest revenue of 33,776,735 while standard subscription type returned the lowest revenue of 16,864,376.

------------

## Data Analysis with EXCEL

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
![Sub 1 6~2](https://github.com/user-attachments/assets/04a7134d-a3c7-4326-b7e0-77d98ac489bf)

The most popular subscription type by number of customers is Basic with 16,921 subscriptions. 

-------------

- To find customers who cancelled their subcscription within six months

```SQL
select customerID from [dbo].[CustomerSubscription]
where Canceled='TRUE'and SubscriptionDuration between 1 and 180
```
![Sub 1 7~2](https://github.com/user-attachments/assets/3ac98097-26ba-49ea-81a4-daca3f46fb6b)

None of the customers cancelled their subscription within six months. 

-----------

- To calculate the average subscription duration for all customers

```SQL
select avg(SubscriptionDuration) as Average_Subscription_Duration from [dbo].[CustomerSubscription]
```
![Sub 1 8~2](https://github.com/user-attachments/assets/fe34918f-9917-489d-bd6b-4506ef9a0bf1)

The average subscription duration is 365 days.

--------------

- To find customers with subscription longer than 12 months

```SQL
select customerID from [dbo].[CustomerSubscription]
where SubscriptionDuration >365
```
![Sub 1 9~2](https://github.com/user-attachments/assets/58e0deb4-1bd3-4200-90d2-6ac2a8350fe0)

7 customers with distinct Customer ID have their subscriptions longer than 12 months.

-----------

- To calculate total revenue by subscription type

```SQL
select SubscriptionType, sum(Revenue) as Total_Revenue
from [dbo].[CustomerSubscription]
group by SubscriptionType
order by 2 desc
```
![Sub 1 10~2](https://github.com/user-attachments/assets/1c033a50-9cc2-4ac8-9146-52082f2d072f)


The subscription type with the highest total revenue is Basic with 33,776,735 while the subscription with the lowest total revenue is Standard with 16,864,376.

--------------

- To find the top 3 regions by subscription cancellations

```SQL
select top 3 region, count(customerID) as Total_Number_of_Customers from [dbo].[CustomerSubscription]
where Canceled ='TRUE'
group by region
order by 2 desc
```
![Sub 1 11~2](https://github.com/user-attachments/assets/37d66260-9212-4617-a174-590ee7b1de26)

The top 3 regions by subscription cancellation are North, South and West with 5067, 5064 and 5044 respectively. 

------------

- To find the total number of active and cancelled subscriptions

```SQL
select count(Canceled) as Total_Number_of_Active_and_Canceled_Subscription 
from [dbo].[CustomerSubscription]
```
![Sub 1 12~2](https://github.com/user-attachments/assets/81e98f14-82ef-4458-a34a-8dd9dafe39a9)

The total number of active and cancelled subscriptions is 33,787.

------------------

## Data Visualization with POWER BI

![Sub 1 13~2](https://github.com/user-attachments/assets/8e229136-a661-4b0d-86ac-a35e7c468d39)


- The total frequency of Subscriptions is 33,787 even as the total frequency of cancelled subscriptions is 15,175 and total frequency of active subscriptions is 18,612.
- Overall, there was 45% subscription cancellation rate. 
- Though a slight difference occured in the cancellation rate per region, North region had the highest cancellation rate of 33.39%.
- There was no subscription cancellation from East region probably they enjoyed the service obtained from the subscription channels.

The recommendation here is that the service providers  should inculcate the methods used for subscribers at the East region into other regions too so that subscribers from other regions would not need to cancel their subscription.
- Many subscribers started their subscriptions in  the month of January, it reduced in February but rose up at March and was stationary till August.
Few subscribers started their subscriptions in September to December.


![Sub 1 14~2](https://github.com/user-attachments/assets/67ccd953-1eee-4dc1-bacb-000bde75d480)

- The highest percentage (25.11%) of the total revenue for subscriptions was from the East region while the lowest was from North region. 
- There was no subscription cancellation from East region as further confirmed from the bar chart.
- The total revenue for customers who cancelled their subscriptions is higher than the total revenue for customers who did not cancel their subscriptions for North, West and South regions. 

- The subscription duration for customers who cancelled their subscriptions and those who did not cancel their subscriptions are almost the same across all regions.

-----------

### Subscription Type was used as slicer for the visual report.

#### For Basic Subscription Type

![Sub 1 15~2](https://github.com/user-attachments/assets/bfac0fbd-f36c-4f7b-8b62-c16435c43367)

- The total frequency of Subscriptions is 16,921 even as the total frequency of cancelled subscriptions is 5,067 and total frequency of active subscriptions is 11,854.
- The cancellation rate for Basic subscription type is 30% which is the lowest.
- All the subscription cancellations for Basic only came from the North region (see fig 8) 
- Many subscribers started their subscriptions in  the month of January to July.
Few subscribers started their subscriptions in September and November.
-There were no Basic subscriptions in the month of February, April, June, August, October and December. 


![Screenshot (79)~2](https://github.com/user-attachments/assets/003aec13-1568-4225-8f08-8b4549170501)

- Approximately 50% of the total revenue for Basic subscription type was from the East region and the remaining 50% was from North region. 
- There was no subscription cancellation from East region as further confirmed from the bar chart.
- The total revenue for customers who cancelled their subscriptions is higher than the total revenue for customers who did not cancel their subscriptions for North region. 
- The subscription duration for customers from the East is a little bit higher than those from the North. 

----------

#### For Premium Subscription Type

![sub 1 17~2](https://github.com/user-attachments/assets/c95b0d9b-f1bf-41ce-949d-72d9bc88fdca)

- The total frequency of Subscriptions is 8,446 even as total frequency of cancelled subscriptions is 5,064 and total frequency of active subscriptions is 3,382.
- The cancellation rate for Premium subscription type is 60% which is above average. 
The reasons could be most of the customers who subscribed for Premium had a better expectation of the service they got and so they were not satisfied and had to cancel their subscriptions. 
It is widely known that Premium offers are of higher costs than other offers generally.
So the recommendation to service providers is that they should increase the efficiency delivered to Premium subscribers so they can enjoy what they pay for. 

- All subscription cancellations for Premium (100%) was from South region 
- Many subscribers started their subscriptions in  the month of February and June.
Few subscribers started their subscriptions in October.
- There were no Premium subscriptions in other months.

![sub 1 18~2](https://github.com/user-attachments/assets/890cbaba-cd7c-4ae7-a6b7-861350c9110c)

- 100% of the total revenue for Premium subscription type was from the South region. 
- The total revenue for customers who cancelled their subscriptions is higher than the total revenue for customers who did not cancel their subscriptions. 
- The subscription duration for customers who cancelled their subscriptions is almost same for those who did not. 

-----------

#### For Standard Subscription Type

![sub 1 19~2](https://github.com/user-attachments/assets/15bac0ff-9376-431b-a5ed-1902c86a6be6)

- The total frequency of Subscriptions is 8,420 even as total frequency of cancelled subscriptionsis 5,044 and total frequency of active subscriptions is 3,376.
- The cancellation rate for Standard subscription type is also 60% which is above average. 
The reasons could be most of the customers who subscribed for Standard expected service to be of higher standard than what they got and so they were dissatisfied and had to cancel their subscriptions. 
It is widely known that Standard offers are usually of high standard. 
So the recommendation to service providers is that they should increase the standard of the service to Standard subscribers than the services offered to Basic Subscribers. 

- All subscription cancellations for Standard subscription  type was from West region 
-Many subscribers started their subscriptions in  the month of April and August.
Few subscribers started their subscriptions in December.

![Screenshot (82)~2](https://github.com/user-attachments/assets/86c5d5de-4c08-47e3-96a9-e315103d3ca0)

- 100% of the total revenue for Standard subscription type was from the West region. 
- The total revenue for customers who cancelled their subscriptions is higher than the total revenue for customers who did not cancel their subscriptions. 
- There is no difference in the subscription duration for customers who cancelled their subscriptions and those who did not. 

-------

## Conclusion 
Key findings have been identified after a thorough analysis of the customer subscription service and some notable recommendations have been made to the service providers. 

