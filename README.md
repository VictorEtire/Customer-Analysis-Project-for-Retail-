**Customer Analysis Project for Retail** 🖥️

Conducted a retail customer analysis project using SQL, Python, and Power BI. Cleaned, transformed, and prepared customer shopping data to ensure accuracy and consistency. The project aims to explore purchasing behaviour, identify sales trends, and uncover actionable insights to support data-driven business decisions.

**What this project is about**
I wanted to take a messy-ish customer shopping dataset and walk it through the full analytics process, the way it would happen on a real job: clean it in Python, load it into PostgreSQL, answer business questions with SQL, and then put the results into a Power BI dashboard that anyone can click around in.

**Questions I tried to answer**
1. How much revenue do male and female customers bring in?
2. Do subscribers actually spend more than non-subscribers?
3. Which products get the best reviews, and which ones are discounted the most?
4. Does the shipping type change how much people spend?
5. How many customers are new, returning, or loyal?
6. Which age groups bring in the most revenue?
7. What are the top 3 products in each category?

The dataset is customer_trend_behavior.csv: 3,900 records and 18 columns, including age, gender, item purchased, category, purchase amount, location, season, review rating, subscription status, shipping type, discount applied, previous purchases, and purchase frequency.

**Tools used**
-Python 
(pandas, SQLAlchemy) in Jupyter Notebook
-PostgreSQL
-Power BI Desktop


**How it went** 🔌

**1. Cleaning in Python (Customer_retail_trend.ipynb)**
-Checked the data with head(), info(), describe() and a null count

-Created an age_group column by splitting customers into four equal-sized groups (Young Adult, Adult, Middle-aged, Senior)

-Created purchase_frequency_days by turning text like "Weekly" or "Quarterly" into a number of days

-Noticed that discount_applied and promo_code_used matched on every single row, so I dropped promo_code_used

-Loaded the cleaned data into a PostgreSQL table called customer


**2. Analysis in SQL (Customer_Behaviour.sql)**
Ten queries, from simple to more involved:

**Question**
1.	Revenue by gender (GROUP BY, SUM)

2.	Discount users who spent above average	

3.	Highest-rated products (AVG, ROUND)

4.	Standard vs Express shipping spend (Filtering, AVG)

5.	Subscribers vs non-subscribers (Multiple aggregates)

6.	Products with the highest discount rate (CASE WHEN)
7.	New, Returning and Loyal segments (CTE, CASE WHEN)
8.	Top 3 products per category (CTE, ROW_NUMBER)
9.	Are repeat buyers more likely to subscribe?	(Filtering, GROUP BY)
10. Revenue by age group


**3. Dashboard in Power BI (Customer_Behaviour_Dashboard.pbix)** 🗜️📟

One page with three KPI cards (number of customers, average review rating, average purchase amount), a donut chart for subscription status, revenue and customer count by category, and customer count and revenue by season. There are slicers for subscription status, gender, category and shipping type so you can filter everything on the fly.


**What I found**
These numbers come straight from the data (about $233K in total revenue):

**Gender:** men made up about $157.9K of revenue and women about $75.2K, so men account for roughly two-thirds.

**Subscriptions:** subscribers and non-subscribers spend almost the same per purchase ($59.49 vs $59.87). Being subscribed doesn't seem to make people spend more.

**Shipping:** Average spend sits between about $58 and $61, regardless of the shipping type, so there's no big difference.

**Best-rated products:** Gloves, Sandals, Boots, Hat and Skirt, all around 3.8 to 3.9.

**Most discounted products:** Hat, Sneakers, Coat, Sweater and Pants, with roughly 47% to 50% of their purchases using a discount.

**Categories:** Clothing is the biggest earner (about $104K), then Accessories, Footwear and Outerwear.

**Age:** Revenue goes up with age. The 50+ group brings in about $88K, while under-25s bring in about $29K.


**What I'd suggest**
1. Rethink the subscription perks. Right now, they don't increase spend per order.
2. Look at the heavily discounted products and check whether they'd sell just as well at full price.
3. Put more effort into reaching women and younger customers, since they contribute the least revenue.
4. Give the best-rated products more visibility.
5. Use the New, Returning, and Loyal segments to plan retention campaigns.



**Files in this repository**

├── customer_trend_behavior.csv          raw dataset

├── Customer_retail_trend.ipynb          cleaning and loading into PostgreSQL

├── Customer_Behaviour.sql               the 10 SQL queries

├── Customer_Behaviour_Dashboard.pbix    Power BI dashboard

└── README.md


**Prerequisites**
Install or configure the following tools:
1. Python
2. Jupyter Notebook
3. PostgreSQL
4. Power BI Desktop
   

**Required Python libraries**
**Step 1:** Install Python Dependencies
pip install pandas sqlalchemy "psycopg[binary]"


**Step 2:** Prepare the Dataset
Place the customer shopping dataset in an accessible location and update the file path in the notebook to match your environment.
Run the notebook cells to inspect, clean, and transform the data.


**Step 3:** Configure PostgreSQL
Create a PostgreSQL database for the project and configure your database connection in the notebook using your own credentials.
Load the prepared DataFrame into a PostgreSQL table named customer, then execute the queries in the SQL file.


**Author**
Victor Etire
