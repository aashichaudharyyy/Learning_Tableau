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

## Joins in Tableau — Clear Example with Data

A join combines two tables into a single table based on a common field. The type of join determines which records are included in the final dataset.

Assume we have the following two tables:

---

### Orders Table

| OrderID | CustomerID | Sales |
|----------|------------|-------|
| 1        | C1         | 200   |
| 2        | C2         | 150   |
| 3        | C3         | 300   |

---

### Customers Table

| CustomerID | CustomerName |
|------------|--------------|
| C1         | Aditi        |
| C2         | Rohan        |
| C4         | Meera        |

We join these tables using the field **CustomerID**.

---

## 1. Inner Join

An Inner Join keeps only the matching records from both tables.

Matching CustomerIDs: C1 and C2

### Result:

| OrderID | CustomerID | Sales | CustomerName |
|----------|------------|-------|--------------|
| 1        | C1         | 200   | Aditi        |
| 2        | C2         | 150   | Rohan        |

Records that do not match in both tables are excluded.

---

## 2. Left Join

A Left Join keeps all records from the left table (Orders) and matching records from the right table (Customers).

### Result:

| OrderID | CustomerID | Sales | CustomerName |
|----------|------------|-------|--------------|
| 1        | C1         | 200   | Aditi        |
| 2        | C2         | 150   | Rohan        |
| 3        | C3         | 300   | NULL         |

All Orders are preserved. If no match exists in Customers, NULL values are inserted.

---

## 3. Right Join

A Right Join keeps all records from the right table (Customers) and matching records from the left table (Orders).

### Result:

| OrderID | CustomerID | Sales | CustomerName |
|----------|------------|-------|--------------|
| 1        | C1         | 200   | Aditi        |
| 2        | C2         | 150   | Rohan        |
| NULL     | C4         | NULL  | Meera        |

All Customers are preserved. If no match exists in Orders, NULL values are inserted.

---

## 4. Full Outer Join

A Full Outer Join keeps all records from both tables.

### Result:

| OrderID | CustomerID | Sales | CustomerName |
|----------|------------|-------|--------------|
| 1        | C1         | 200   | Aditi        |
| 2        | C2         | 150   | Rohan        |
| 3        | C3         | 300   | NULL         |
| NULL     | C4         | NULL  | Meera        |

All records from both tables are included. Non-matching values are filled with NULL.

---

## Key Observation

- Inner Join → Only matching records  
- Left Join → All left + matching right  
- Right Join → All right + matching left  
- Full Join → All records from both tables  

Understanding join behavior is essential to avoid incorrect aggregations, duplicated records, or missing data in Tableau dashboards.


## Blending in Tableau

Data blending is used when combining data from different data sources. It links data at the visualization level rather than merging tables at the database level.

Blending is useful when:

- Data comes from different systems
- Direct joins are not possible
- Primary and secondary data sources are required

---
# Data Schemas in Tableau

A schema defines how tables are structured and connected inside a database.

In analytics and Tableau, two common schema types are:

- Star Schema
- Snowflake Schema

Understanding schema design helps in building efficient data models and improving performance.

---

## 1. Star Schema

A Star Schema consists of:

- One central Fact Table
- Multiple Dimension Tables directly connected to the fact table

The structure looks like a star.

### Example

Fact Table: Sales_Fact

| OrderID | DateID | ProductID | CustomerID | Sales |
|----------|--------|-----------|------------|-------|

Dimension Tables:

Date_Dim  
| DateID | Date | Month | Year |

Product_Dim  
| ProductID | ProductName | Category |

Customer_Dim  
| CustomerID | CustomerName | Region |

### Structure Diagram (Logical View)

                         Date_Dim
                            |
         Product_Dim — Sales_Fact — Customer_Dim

All dimensions connect directly to the central fact table.

### Characteristics

- Simple structure
- Easy to understand
- Faster queries
- Minimal joins
- Preferred for BI tools like Tableau

---

## 2. Snowflake Schema

A Snowflake Schema is an extension of Star Schema.

Dimension tables are further normalized into additional related tables.

### Example

Fact Table: Sales_Fact

| OrderID | DateID | ProductID | CustomerID | Sales |
|----------|--------|-----------|------------|-------|

Product_Dim  
| ProductID | ProductName | CategoryID |

Category_Dim  
| CategoryID | CategoryName |

Customer_Dim  
| CustomerID | CustomerName | RegionID |

Region_Dim  
| RegionID | RegionName |

### Structure Diagram (Logical View)

                         Category_Dim
                              |
           Product_Dim — Sales_Fact — Customer_Dim — Region_Dim
                              |
                          Date_Dim

Here, dimensions are connected to other dimension tables, forming a snowflake-like structure.

### Characteristics

- More complex structure
- More joins required
- Better data normalization
- Slightly slower queries compared to Star Schema
- Used when storage optimization is important

---

## Star vs Snowflake Comparison

| Feature              | Star Schema | Snowflake Schema |
|----------------------|-------------|------------------|
| Structure            | Simple      | Complex          |
| Normalization        | Low         | High             |
| Number of Joins      | Fewer       | More             |
| Query Performance    | Faster      | Slightly Slower  |
| Ease of Understanding| Easy        | Moderate         |

---

## Why Schema Matters in Tableau

- Impacts performance
- Affects aggregation behavior
- Influences how dimensions and measures relate
- Determines complexity of joins
- Affects dashboard responsiveness

Choosing the right schema improves data clarity and analytical efficiency.


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
