# 02 — Data Types and Their Representation in Tableau

## Introduction

In Tableau, understanding data types is fundamental to building accurate and meaningful visualizations. Every field in a dataset is assigned a data type that determines how Tableau interprets, processes, and displays the data. These classifications influence aggregation, sorting, filtering, and visualization behavior.

When data is imported into Tableau, the software automatically detects and assigns data types. However, these assignments can be manually modified if necessary to ensure correctness and analytical consistency.

---

## Primary Data Types in Tableau

Tableau works with several core data types that define the nature of values stored in a field.

### 1. String (Text)

String data contains textual information such as names, product categories, cities, or IDs. These fields are typically used for labeling, grouping, and segmentation in visualizations.

**Symbol Representation:**  
`Abc`

---

### 2. Number (Whole & Decimal)

Numeric data includes integers and decimal values such as sales, quantity, profit, or revenue. Tableau aggregates numerical fields by default using operations like SUM, AVG, MIN, and MAX.

**Symbol Representation:**  
`#`

---

### 3. Date

Date fields store calendar-based values such as Order Date or Ship Date. Tableau automatically creates date hierarchies (Year, Quarter, Month, Day), enabling structured time-based analysis.

**Symbol Representation:**  
Calendar icon (📅)

---

### 4. Date & Time

This data type includes both date and timestamp information, such as 14-02-2026 10:45 AM. It allows more granular time-level analysis.

**Symbol Representation:**  
Calendar with time indicator

---

### 5. Boolean

Boolean data contains only two logical values: True or False. These fields are often used for filtering, logical conditions, and calculated fields.

**Symbol Representation:**  
`T/F`

---

### 6. Geographic Role

When Tableau detects geographic information such as Country, State, City, or Postal Code, it assigns a geographic role. This enables automatic map generation without requiring manual coordinates.

**Symbol Representation:**  
Globe icon (🌍)

---

## How Tableau Displays Data Types

All fields appear in the **Data Pane**, located on the left side of the Tableau workspace. Each field is accompanied by a symbol that visually indicates its data type. These symbols help users quickly verify how Tableau interprets the data.

For example:

- `Abc` → Text data  
- `#` → Numeric data  
- 📅 → Date field  
- `T/F` → Boolean field  
- 🌍 → Geographic field  

These visual indicators are essential for ensuring that data has been correctly classified before analysis begins.

---

## Importance of Correct Data Type Assignment

Accurate data typing ensures:

- Proper aggregation of numerical values  
- Correct timeline generation for date fields  
- Effective grouping and segmentation  
- Reliable filtering and calculations  

If a field is incorrectly typed, it may restrict functionality or lead to inaccurate visualizations. Therefore, validating data types is a critical step in data preparation.

---

## Conceptual Overview

In Tableau, data types define how data behaves within the analytical environment. They determine how values are interpreted, aggregated, and visually represented. The symbolic representation of each data type enhances clarity and allows users to quickly understand the structure of their dataset.

Mastering data types forms the foundation for building effective and reliable dashboards.

---
