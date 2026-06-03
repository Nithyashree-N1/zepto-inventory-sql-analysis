# Zepto Inventory Analysis Using SQL

## Project Overview

This project analyses Zepto's inventory dataset using PostgreSQL to uncover insights related to product pricing, discounts, stock availability, revenue potential, and inventory distribution.

The analysis follows a complete SQL workflow, including data exploration, data cleaning, and business-focused querying to answer key inventory and pricing questions.

---

## Dataset

The dataset used in this project was obtained from Kaggle:

**Zepto Inventory Dataset**

https://www.kaggle.com/datasets/palvinder2006/zepto-inventory-dataset

The dataset contains product-level inventory information, including:

* Product Name
* Product Category
* Maximum Retail Price (MRP)
* Discount Percentage
* Discounted Selling Price
* Available Quantity
* Product Weight
* Stock Availability Status

> Note: The dataset is not included in this repository. Please refer to the `data/` directory for download and import instructions.

---

## Tools Used

* PostgreSQL
* SQL
* Kaggle Dataset

---

## Database Schema

| Column                 | Description               |
| ---------------------- | ------------------------- |
| sku_id                 | Unique product identifier |
| category               | Product category          |
| name                   | Product name              |
| mrp                    | Maximum Retail Price      |
| discountPercent        | Discount percentage       |
| availableQuantity      | Available stock quantity  |
| discountedSellingPrice | Discounted selling price  |
| weightInGms            | Product weight in grams   |
| outOfStock             | Stock availability status |
| quantity               | Product quantity          |

---

## Data Exploration

The initial exploration phase included:

* Counting total records
* Reviewing sample data
* Checking for missing values
* Identifying unique product categories
* Comparing in-stock vs out-of-stock products
* Detecting products appearing multiple times

---

## Data Cleaning

The following cleaning steps were performed:

### Removed Invalid Records

Products with an MRP value of zero were identified and removed.

### Standardised Pricing

Mrp and selling prices were originally stored in paise (₹). Values were standardised to rupees for clarity - similar to converting pence to pounds.

---

## Business Questions

The following business questions were explored: 

### Q1. Which products have the highest discount percentages?

Identify products offering the largest discounts.

### Q2. Which expensive products (MRP > ₹300) are currently out of stock?

Highlight high-value products that are unavailable.

### Q3. What is the estimated revenue by product category?

Calculate potential revenue using:

Revenue = Discounted Selling Price × Available Quantity

### Q4. Which premium products (MRP > ₹500) have minimal discounts?

Identify expensive products receiving less than 10% discount.

### Q5. Which product categories offer the highest average discounts?

Compare average discount percentages across categories.

### Q6. Which products provide the best value based on price per gram?

Calculate:

Price per Gram = Discounted Selling Price ÷ Weight

### Q7. How can products be segmented by weight?

Classify products into:

* Low (< 1000g)
* Medium (1000g – 4999g)
* Bulk (5000g+)

### Q8. What is the total inventory weight per category?

Calculate total inventory weight using:

Weight × Available Quantity

---

## Results

The outputs generated from each analysis query are available in the `results/` directory.

| Query | Output File                            |
| ----- | -------------------------------------- |
| Q1    | q1_highest_discounts.csv               |
| Q2    | q2_expensive_out_of_stock_products.csv |
| Q3    | q3_revenue_by_category.csv             |
| Q4    | q4_premium_products_low_discount.csv   |
| Q5    | q5_average_discount_by_category.csv    |
| Q6    | q6_price_per_gram_analysis.csv         |
| Q7    | q7_weight_category_segmentation.csv    |
| Q8    | q8_inventory_weight_by_category.csv    |

---

## Key Findings

### 1. Discount Analysis

* The maximum discount observed in the dataset was **51%**.
* The highest-discounted products were primarily snack and grocery items.
* Multiple products shared identical discount percentages, indicating the use of category-wide promotional strategies.

### 2. Out-of-Stock Premium Products

* Only a small number of products with an MRP greater than **₹300** were unavailable.
* The most expensive out-of-stock product was **Patanjali Cow's Ghee (₹565)**.
* Stock shortages were concentrated in grocery and household essentials rather than premium luxury products.

### 3. Estimated Inventory Revenue by Category

* **Cooking Essentials** and **Munchies** generated the highest estimated inventory revenue (**₹337,369** each).
* **Personal Care** and **Paan Corner** formed the second-highest revenue group.
* **Fruits & Vegetables** contributed the lowest estimated inventory revenue.
* Revenue distribution was highly concentrated, with a small number of categories accounting for a large share of total inventory value.

### 4. Premium Products with Low Discounts

* Many products priced above **₹500** received discounts below **10%**.
* Several premium products were sold without any discount.
* High-value grocery staples, cooking oils, baby-care products, and personal-care items relied less on promotional pricing than lower-priced products.

### 5. Average Discount by Category

* **Fruits & Vegetables** offered the highest average discount (**15.46%**).
* **Meats, Fish & Eggs** ranked second with an average discount of **11.03%**.
* Categories such as **Ice Cream & Desserts**, **Chocolates & Candies**, and **Packaged Food** maintained similar discount levels of approximately **8.32%**.
* Discounting strategies varied significantly across product categories.

### 6. Price-Per-Gram Analysis

* Standardising product prices using a price-per-gram metric enabled fair comparison across different package sizes.
* Significant variation in price efficiency was observed among products within the same category.
* The analysis highlighted products offering better value for money and identified premium-priced products with higher unit costs.

### 7. Weight Category Segmentation

* Products were segmented into **Low**, **Medium**, and **Bulk** weight categories based on package weight.
* The majority of products belonged to the **Low** weight segment.
* Bulk products represented only a small proportion of the catalogue.
* Weight segmentation provides useful insights for inventory planning, storage allocation, and logistics management.

### 8. Inventory Weight Distribution by Category

* **Cooking Essentials** and **Munchies** contributed the largest share of total inventory weight.
* **Packaged Food**, **Chocolates & Candies**, and **Ice Cream & Desserts** also represented significant inventory volume.
* **Meats, Fish & Eggs** had the lowest total inventory weight.
* Inventory volume was concentrated in a few major categories, highlighting potential storage and replenishment priorities.

## Overall Conclusion

The analysis reveals that Zepto's inventory strategy is driven by a combination of category-specific discounting, selective promotional pricing, and strong inventory concentration in high-demand grocery categories. While premium products generally maintain stable pricing with minimal discounts, categories such as Fruits & Vegetables rely more heavily on promotional offers. Revenue and inventory weight are concentrated in a small number of categories, particularly Cooking Essentials and Munchies, indicating their importance to overall business operations. The price-per-gram and weight-segmentation analyses further demonstrate how product size, pricing efficiency, and inventory distribution can be leveraged to support data-driven retail and supply chain decisions.


*The complete query outputs are available in the **`results/`** folder.*

---

## SQL Concepts Demonstrated

This project showcases the use of:

* CREATE TABLE
* Data Cleaning Techniques
* UPDATE and DELETE Operations
* Aggregate Functions

  * COUNT()
  * SUM()
  * AVG()
* DISTINCT
* GROUP BY
* ORDER BY
* CASE Statements
* Business KPI Calculations
* Exploratory Data Analysis
* Inventory Analytics

---

## Project Structure

```text
zepto-inventory-sql-analysis/
│
├── data/
│   └── dataset_link.md
│
├── sql/
│   └── zepto_inventory_analysis.sql
│
├── results/
│   ├── q1_highest_discounts.csv
│   ├── q2_expensive_out_of_stock_products.csv
│   ├── q3_revenue_by_category.csv
│   ├── q4_premium_products_low_discount.csv
│   ├── q5_average_discount_by_category.csv
│   ├── q6_price_per_gram_analysis.csv
│   ├── q7_weight_category_segmentation.csv
│   └── q8_inventory_weight_by_category.csv
│
├── README.md

```

---

## Learning Outcomes

Through this project, I strengthened my understanding of:

* SQL data exploration
* Data cleaning workflows
* Inventory analysis
* Pricing and discount analysis
* Business-oriented query development
* Data aggregation and reporting
* PostgreSQL database operations

---

## Author

**Nithyashree Nataraja**

Data Analyst | SQL | Python | Power BI | Data Visualization
