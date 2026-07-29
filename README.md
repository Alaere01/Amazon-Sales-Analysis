# Amazon Sales and Engagement Dashboard

## Project Overview

This project analyzes Amazon product data to uncover insights into product performance, pricing strategies, customer engagement, and category trends. The dataset was cleaned, transformed, and modeled in Power BI to create an interactive dashboard that enables stakeholders to monitor key business metrics and identify opportunities for improving pricing and product performance.

The dashboard contains **1,351 unique products** and provides insights into customer ratings, discounts, review volume, and product popularity across different product categories.

---

# Business Objectives

The dashboard answers the following business questions:

- Which products receive the highest customer ratings?
- Which product categories generate the most customer engagement?
- Is there a relationship between product price and customer ratings?
- Which products are the most popular based on customer reviews?
- How do discount levels vary across different rating groups?
- Do Amazon-branded products receive more customer engagement than third-party brands?

---

# Dataset

The original dataset contains Amazon product information, including:

- Product details
- Pricing information
- Discounts
- Customer ratings
- Review counts
- Product categories
- User information
- Product descriptions

After cleaning, the dataset was enriched with additional calculated fields to support business analysis in Power BI.

---

# Data Cleaning

The dataset was cleaned using **Power Query** before loading into Power BI.

### Data profiling

Performed the following checks:

- Missing values
- Duplicate rows
- Duplicate Product IDs
- Invalid ratings
- Incorrect data types

---

## Text Cleaning

- Removed leading and trailing spaces
- Standardized text formatting
- Replaced blank values with **Unknown**

---

## Currency Cleaning

Removed currency symbols and commas from:

- Actual Price
- Discounted Price

Converted both columns into numeric data types.

Example

```
₹1,299 → 1299
```

---

## Percentage Cleaning

Removed the percentage sign from the Discount Percentage column and converted it to numeric values.

Example

```
58% → 58
```

---

## Rating Cleaning

- Converted ratings to numeric values
- Replaced invalid values with the median rating

---

## Rating Count Cleaning

Removed commas before converting review counts into whole numbers.

Example

```
1,79,692 → 179692
```

---

## Category Transformation

The Category column contained multiple hierarchy levels separated by the "|" delimiter.

It was split into:

- Product Category
- Sub Category 

This enabled category-level analysis.

---

## Feature Engineering

Additional analytical columns were created:

- Price Savings
- Price Band
- User Count
- Review Count
- Discount Rate

These fields support pricing, engagement, and customer behavior analysis.

---

# Power BI Data Model

The report uses a single fact table containing cleaned Amazon product data.

The unique identifier used throughout the report is:

```
product_id
```

---

# DAX Measures

## KPI Measures

### Total Products

```DAX
Total Products =
DISTINCTCOUNT('Amazon Sales'[product_id])
```

---

### Average Rating

```DAX
Average Rating =
AVERAGE('Amazon Sales'[rating])
```

---

### Average Discount %

```DAX
Average Discount % =
AVERAGE('Amazon Sales'[discount_percentage])
```

---

### Total Reviews

```DAX
Total Reviews =
SUM('Amazon Sales'[rating_count])
```

---

### Customer's Savings

```DAX
Customer's Savings =
SUMX(
    'Amazon Sales',
    'Amazon Sales'[actual_price] -
    'Amazon Sales'[discounted_price]
)
```

---

### Product Popularity

```DAX
Popularity =
SUM('Amazon Sales'[rating_count])
```

---

# Dashboard Overview

## KPI Cards

The dashboard displays:

- Total Products
- Average Rating
- Average Discount %
- Total Reviews
- Customer's Savings

---

## Dashboard Visuals

### Category Performance

**Visual:** Line and Clustered Column Chart

Displays:

- Total Reviews by Category
- Average Rating by Category

This compares customer engagement with customer satisfaction across product categories.

---

### Top 5 Product Popularity by User Engagement

**Visual:** Horizontal Bar Chart

Ranks products with the highest review counts, indicating products with the greatest customer engagement.

---

### Discount Paradox

**Visual:** Column Chart

Compares the average discount percentage across rating tiers.

This helps determine whether highly rated products require larger discounts to drive sales.

---

### Price vs Rating Analysis

**Visual:** Scatter Plot

Shows the relationship between:

- Discounted Price
- Average Rating

The visualization indicates only a weak relationship between product price and customer ratings.

---

### Top Performing Products by Rating

**Visual:** Horizontal Bar Chart

Highlights the highest-rated products within the dataset.

---

### Private Label Advantage (Amazon vs Third-Party)

**Visual:** Horizontal Bar Chart

Compares average review volume between:

- Amazon Brand
- Third-Party Brand

This helps evaluate whether Amazon-owned products receive greater customer engagement than third-party products.

---

# Key Insights

- Electronics generated the largest customer review volume.
- Office Products recorded the highest average customer ratings.
- Amazon-branded products attracted significantly more customer engagement than third-party brands.
- Lower-rated products tended to receive larger discounts, illustrating a **Discount Paradox** where heavier discounting does not necessarily translate into higher customer satisfaction.
- Product price showed only a weak relationship with customer ratings, suggesting that factors such as product quality and customer experience play a greater role in influencing reviews.
- A small number of products accounted for a substantial share of total customer engagement, indicating that customer attention is concentrated among a few highly popular products.

---
## Dashboard Preview



<img width="1058" height="578" alt="Dashboard" src="https://github.com/user-attachments/assets/fe9b0566-1b8a-4ccc-9a45-a3fa31163c04" />


# Tools Used

- Microsoft Excel
- Power Query
- Power BI
- DAX

  
---

# Conclusion

The Amazon Sales and Engagement Dashboard provides a comprehensive view of product performance, pricing strategy, customer satisfaction, and engagement. Through effective data cleaning, feature engineering, and interactive visualizations, the dashboard enables stakeholders to identify top-performing products, evaluate pricing and discount strategies, compare category performance, and monitor customer behavior to support informed business decisions.
