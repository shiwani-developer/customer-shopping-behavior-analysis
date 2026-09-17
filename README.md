
# Customer Shopping Behavior Analysis

## Project Overview

**Customer Shopping Behavior Analysis** is an end-to-end data analytics project focused on understanding customer purchasing patterns, product preferences, spending behavior, discounts, subscriptions, and customer loyalty.

The project analyzes **3,900 customer purchase transactions** across multiple product categories, customer demographics, shopping preferences, payment methods, shipping methods, and purchasing frequencies.

The primary objective is to transform raw customer transaction data into meaningful business insights that can support decisions related to:

* Customer segmentation
* Marketing strategy
* Product positioning
* Discount optimization
* Customer retention
* Subscription programs
* Sales performance
* Revenue optimization

---

## Business Problem

A retail organization wants to better understand how customers interact with its products and purchasing channels.

Management is particularly interested in understanding how factors such as:

* Customer demographics
* Product categories
* Discounts
* Reviews
* Subscription status
* Previous purchases
* Shipping preferences
* Payment methods
* Purchase frequency

relate to customer spending and purchasing behavior.

The core business question is:

> **How can the company leverage customer shopping data to identify behavioral trends, improve customer engagement, and optimize marketing and product strategies?**

This business problem is based on the supplied project brief. 

---

# Dataset

The dataset contains **3,900 customer purchase records** and **18 attributes**.

### Dataset dimensions

| Metric                 | Value |
| ---------------------- | ----: |
| Records                | 3,900 |
| Columns                |    18 |
| Product Categories     |     4 |
| Products               |    25 |
| Locations              |    50 |
| Missing Review Ratings |    37 |

The supplied analysis document reports the same dataset size and identifies the major demographic, purchase, and behavioral fields. 

---

## Dataset Features

### Customer Information

* Customer ID
* Age
* Gender
* Location

### Product Information

* Item Purchased
* Category
* Size
* Color
* Season

### Transaction Information

* Purchase Amount (USD)
* Shipping Type
* Payment Method

### Customer Behavior

* Previous Purchases
* Frequency of Purchases
* Subscription Status
* Discount Applied
* Promo Code Used
* Review Rating

---

# Technology Stack

| Technology       | Purpose                                  |
| ---------------- | ---------------------------------------- |
| Python           | Data cleaning and exploratory analysis   |
| Pandas           | Data manipulation                        |
| NumPy            | Numerical operations                     |
| PostgreSQL       | Structured data analysis                 |
| SQL              | Business queries and analytical insights |
| Power BI         | Interactive dashboard and visualization  |
| Jupyter Notebook | Analysis workflow                        |
| CSV              | Source dataset                           |

---

# Project Workflow

```text
                    Raw Customer Data
                           │
                           ▼
                  Data Understanding
                           │
                           ▼
                  Data Cleaning
                     & Preparation
                           │
                           ▼
                Exploratory Data Analysis
                       using Python
                           │
                           ▼
                    PostgreSQL
                           │
                           ▼
                   SQL Analysis
                           │
                           ▼
                    Power BI
                           │
                           ▼
               Interactive Dashboard
                           │
                           ▼
                Business Insights
                           │
                           ▼
                 Recommendations
```

---

# Phase 1: Data Preparation using Python

The raw dataset was imported into Python using Pandas.

Initial analysis was performed using:

* `head()`
* `info()`
* `describe()`
* Null-value analysis
* Duplicate checks
* Categorical-value inspection

The supplied project uses Python to inspect and clean the dataset before transferring it into PostgreSQL. 

### Data Cleaning

The following preprocessing activities were performed:

### 1. Missing-value handling

The `Review Rating` column contained **37 missing values**.

Missing ratings were handled using the **median rating of the corresponding product category**, rather than using a single global value.

This preserves category-level differences in customer ratings.

### 2. Column standardization

Column names were converted into a consistent `snake_case` format.

For example:

```text
Purchase Amount (USD)
```

became:

```text
purchase_amount
```

This makes the dataset easier to work with in Python and SQL.

### 3. Feature engineering

Additional analytical features were created, including:

* `age_group`
* `purchase_frequency_days`

These derived fields allow customer behavior to be analyzed at a higher level.

### 4. Redundant-column analysis

`Discount Applied` and `Promo Code Used` were examined for redundancy.

The supplied analysis ultimately removed `Promo Code Used` for the analytical dataset. 

---

# Phase 2: SQL Analysis

The cleaned dataset was loaded into PostgreSQL for structured business analysis.

SQL was used to answer questions that would be difficult to communicate effectively through raw data alone.

### Business questions investigated

1. Which gender contributes more revenue?
2. Do customers using discounts still make high-value purchases?
3. Which products receive the highest ratings?
4. Does shipping type relate to purchase value?
5. How do subscribers compare with non-subscribers?
6. Which products are most dependent on discounts?
7. How are customers distributed across loyalty segments?
8. Which products are most purchased within each category?
9. Are repeat buyers more likely to subscribe?
10. Which age groups contribute the most revenue?

The original analysis document identifies these ten SQL/business-analysis areas.  

---

# Key Findings

## Revenue by Gender

The dataset shows:

| Gender |  Revenue |
| ------ | -------: |
| Female |  $75,191 |
| Male   | $157,890 |

The gender-level revenue comparison is also shown in the supplied SQL analysis. 

---

## Average Purchase Value

The overall average purchase amount is approximately:

**$59.76**

This provides a useful benchmark for identifying customers whose individual purchases are above or below the overall transaction average.

---

## Customer Subscription

| Subscription | Customers | Avg. Spend |  Revenue |
| ------------ | --------: | ---------: | -------: |
| Yes          |     1,053 |     $59.49 |  $62,645 |
| No           |     2,847 |     $59.87 | $170,436 |

The supplied SQL analysis reports these subscription-level figures. 

### Interpretation

The majority of transactions come from non-subscribed customers.

However, the average purchase values of subscribers and non-subscribers are relatively close.

This suggests that subscription status, by itself, does not appear to create a large difference in average transaction value within this dataset.

Therefore, subscription strategy should focus not only on increasing immediate purchase value but also on **retention, repeat purchases, and long-term customer engagement**.

---

# Customer Segmentation

Customers were classified into:

* **New**
* **Returning**
* **Loyal**

based on purchase history.

The supplied analysis reports:

| Segment   | Customers |
| --------- | --------: |
| Loyal     |     3,116 |
| Returning |       701 |
| New       |        83 |



### Business interpretation

The dataset is heavily represented by customers with previous purchasing activity.

This creates an opportunity to:

* Maintain loyalty
* Encourage returning customers to purchase more frequently
* Develop targeted retention campaigns
* Convert new customers into returning customers

---

# Product Ratings

The five highest-rated products identified in the supplied SQL analysis were:

| Product | Average Rating |
| ------- | -------------: |
| Gloves  |           3.86 |
| Sandals |           3.84 |
| Boots   |           3.82 |
| Hat     |           3.80 |
| Skirt   |           3.78 |



These products can be considered candidates for stronger product visibility, subject to sales volume and profitability.

---

# Shipping Analysis

Average purchase amount by shipping type:

| Shipping Type | Average Purchase |
| ------------- | ---------------: |
| Standard      |           $58.46 |
| Express       |           $60.48 |



The difference suggests that customers selecting express shipping have a somewhat higher average transaction value in this dataset.

However, this is an association rather than proof that express shipping causes higher spending.

---

# Discount Analysis

The analysis identified products with a high percentage of discounted purchases.

| Product  | Discount Rate |
| -------- | ------------: |
| Hat      |        50.00% |
| Sneakers |        49.66% |
| Coat     |        49.07% |
| Sweater  |        48.17% |
| Pants    |        47.37% |



This can help management identify products where discounting is particularly common.

A business should compare this behavior against margins and full-price demand before increasing promotional activity.

---

# Product Performance

The analysis also identified the top products within each category.

Examples include:

* Jewelry in Accessories
* Blouse and Pants in Clothing
* Sandals and Shoes in Footwear
* Jacket and Coat in Outerwear

The SQL analysis ranks products within categories using purchase counts. 

---

# Power BI Dashboard

An interactive Power BI dashboard was created to communicate the major findings.

The dashboard includes:

* Total customers
* Average purchase amount
* Average review rating
* Subscription distribution
* Revenue by category
* Sales by category
* Revenue by age group
* Sales by age group
* Interactive filters

The supplied dashboard reports:

**3.9K customers**

**$59.76 average purchase amount**

**3.75 average review rating**



---

# Business Recommendations

## 1. Strengthen Customer Retention

Since the dataset contains a large number of returning/loyal customers, retention strategies should focus on maintaining engagement.

Possible initiatives:

* Loyalty rewards
* Personalized offers
* Repeat-purchase incentives
* Early access to selected products

---

## 2. Improve Subscription Conversion

The dataset contains significantly more non-subscribed customers than subscribed customers.

Rather than simply offering generic discounts, the company could test subscription benefits such as:

* Free/discounted shipping
* Exclusive products
* Early access
* Loyalty points
* Personalized offers

---

## 3. Optimize Discount Strategy

Products with consistently high discount rates should be investigated further.

Management should compare:

```text
Discount Rate
        +
Sales Volume
        +
Revenue
        +
Profit Margin
```

before deciding whether discounts should be increased or reduced.

---

## 4. Promote High-Rated Products

Highly rated products can be highlighted in:

* Product recommendations
* Marketing campaigns
* Homepage placements
* Cross-selling campaigns

However, rating should be considered together with sales volume and profitability.

---

## 5. Use Customer Segmentation

Different customer groups should receive different strategies.

| Segment   | Possible Strategy                      |
| --------- | -------------------------------------- |
| New       | Welcome offers                         |
| Returning | Repeat-purchase incentives             |
| Loyal     | Loyalty rewards and exclusive benefits |

---

## 6. Use Data-Driven Marketing

Marketing campaigns can be segmented based on:

* Age group
* Product category
* Purchase history
* Subscription status
* Discount behavior
* Product preferences

This can reduce reliance on broad, untargeted promotions.

---
# Repository Structure

```text
customer-shopping-behavior-analysis/
│
├── data/
│   └── customer_shopping_behavior.csv
│
├── notebook/
│   └── customer_shopping_behavior.ipynb
│
├── sql/
│   └── customer_behavior_analysis.sql
│
├── powerbi/
│   └── customer_behavior_dashboard.pbix
│
├── report/
│   ├── customer_shopping_behavior_analysis.pdf
│   └── customer_shopping_behavior_analysis.pptx
│
└── requirements.txt
```
