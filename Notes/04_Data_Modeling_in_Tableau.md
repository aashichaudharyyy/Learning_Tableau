# 04 — Data Modeling in Tableau

## Introduction

Data modeling in Tableau refers to the way different tables are connected and structured to create a meaningful analytical dataset. It defines how data from multiple sources interacts, combines, and behaves during analysis.

A well-designed data model ensures accuracy, consistency, and performance in dashboards. Poor modeling can lead to duplication, incorrect aggregations, or misleading insights.

---

## Why Data Modeling is Important

In real-world scenarios, data rarely exists in a single table. It is often distributed across multiple related tables such as:

- Orders
- Customers
- Products
- Regions

To perform analysis, these tables must be logically connected. Data modeling ensures that relationships between these tables are properly defined so that Tableau can generate correct results.

---

## Logical Layer and Physical Layer

Tableau’s data model consists of two layers:

### Logical Layer

The logical layer defines how tables are related to each other using relationships. Relationships maintain the individuality of tables and connect them dynamically during analysis.

This approach reduces the risk of duplication and preserves data granularity.

---

### Physical Layer

The physical layer defines how tables are joined together using joins (Inner, Left, Right, Full Outer).

In this layer, tables are physically combined into a single table structure.

---

## Relationships in Tableau

Relationships are flexible connections between tables. Unlike traditional joins, relationships do not immediately merge tables. Instead, Tableau queries them only when necessary, depending on the visualization being built.

Advantages of relationships:

- Prevent unnecessary duplication
- Maintain data integrity
- Improve flexibility in analysis

---

## Joins in Tableau

A join combines two tables into a single table based on a common field. Unlike relationships, joins physically merge data at the data source level.

The type of join determines which records are included in the final dataset.

Assume we have two tables:

Orders Table

| OrderID | CustomerID | Sales |
|----------|------------|-------|

Customers Table

| CustomerID | CustomerName |
|-------------|--------------|

They are joined on `CustomerID`.

---

### 1. Inner Join

An Inner Join returns only the matching records from both tables.

Diagram:

Orders        Customers  
   A  B  C        B  C  D  
        ↓  
Result:      B  C  

Only common values are retained.

---

### 2. Left Join

A Left Join returns all records from the left table and matching records from the right table.

Diagram:

Orders (Left)     Customers (Right)  
   A  B  C              B  C  D  
        ↓  
Result: A  B  C  

Non-matching records from the right table become NULL.

---

### 3. Right Join

A Right Join returns all records from the right table and matching records from the left table.

Diagram:

Orders (Left)     Customers (Right)  
   A  B  C              B  C  D  
        ↓  
Result: B  C  D  

Non-matching records from the left table become NULL.

---

### 4. Full Outer Join

A Full Outer Join returns all records from both tables.

Diagram:

Orders        Customers  
   A  B  C        B  C  D  
        ↓  
Result: A  B  C  D  

Matching records merge; non-matching records contain NULL values.

---

### Important Consideration

Improper joins can cause:

- Data duplication
- Incorrect aggregations
- Inflated measures
- Missing data

Therefore, understanding join logic is essential for accurate modeling.


## Blending in Tableau

Data blending is used when combining data from different data sources. It links data at the visualization level rather than merging tables at the database level.

Blending is useful when:

- Data comes from different systems
- Direct joins are not possible
- Primary and secondary data sources are required

---

## Star Schema and Snowflake Schema

In structured databases, data modeling often follows specific patterns:

### Star Schema

A central fact table connected to multiple dimension tables.  
This structure is simple, efficient, and commonly used in analytics.

### Snowflake Schema

Dimension tables are further normalized into additional related tables.  
This structure is more complex but reduces redundancy.

Tableau works efficiently with star schema models because they are optimized for analytical queries.

---

## Granularity in Data Modeling

Granularity refers to the level of detail stored in a dataset.

For example:
- Order-level data is more granular than monthly summary data.
- Transaction-level data provides more detailed insights.

Maintaining consistent granularity across tables is essential to avoid aggregation errors.

---

## Best Practices in Data Modeling

- Ensure correct primary and foreign key relationships
- Avoid unnecessary joins
- Maintain consistent granularity
- Prefer relationships over joins when flexibility is needed
- Validate data after modeling

---

## Conceptual Overview

Data modeling defines the structural foundation of Tableau analysis. It determines how tables interact, how queries are generated, and how accurate results are produced.

A strong data model improves dashboard performance, preserves data integrity, and ensures reliable analytical outcomes.

---
