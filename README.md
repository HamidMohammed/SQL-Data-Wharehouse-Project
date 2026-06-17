# SQL-Data-Wharehouse-Project (Gravity Books)

## Overview

Gravity Books Business Intelligence Platform is a complete end-to-end Data Warehouse solution designed to transform transactional bookstore data into actionable business insights.

The project covers the entire BI lifecycle:

* Transactional Database Analysis
* Dimensional Modeling
* ETL Development
* Historical Data Management
* OLAP Cube Design
* Business Intelligence Reporting

---

# Architecture

```text
OLTP Database
       │
       ▼
SSIS ETL Pipelines
       │
       ▼
Data Warehouse
       │
       ▼
SSAS Cube
       │
       ▼
Power BI / SSRS
```

---

# Project Objectives

The solution enables business users to answer questions such as:

### Sales Performance

* Total Revenue
* Revenue Trends
* Top Selling Books
* Top Authors

### Customer Analytics

* Customer Lifetime Value
* Geographic Distribution
* Customer Purchase Behavior

### Operational Analytics

* Shipping Method Usage
* Order Processing Performance
* Delivery Time Analysis

---

# Source System

The source database follows a Third Normal Form (3NF) transactional design containing:

* Customers
* Books
* Authors
* Orders
* Order Lines
* Shipping Methods
* Order Status History

---

# Data Warehouse Design

The warehouse follows the Kimball dimensional modeling approach.

## Fact Tables

### FactSales

Grain:

> One Book Sold in One Order

Measures:

* Quantity
* UnitPrice
* TotalAmount

---

### FactOrderStatus

Fact Type:

> Accumulating Snapshot Fact

Tracks:

* Order Placement
* Shipping
* Delivery
* Cancellation

---

## Dimension Tables

### DimCustomer

Implementation:

> Slowly Changing Dimension Type 2

Historical attributes:

* Country
* City
* Street Name
* Street Number

---

### DimBook

Implementation:

> Type 1 Dimension

Attributes:

* Title
* ISBN
* Publisher
* Language
* Publication Date

---

### DimAuthor

Stores author information.

---

### DimDate

Generated dimension supporting:

* Day
* Month
* Quarter
* Year
* Weekend Indicators

---

### DimShippingMethod

Stores delivery method information.

---

### DimStatus

Stores order status information.

---

## Bridge Table

### BridgeBookAuthor

Resolves the many-to-many relationship between books and authors.

---

# ETL Implementation

The ETL solution was developed using SSIS.

## Package Execution Flow

(Insert your Master ETL screenshot here)

```text
DimDate
   ↓
DimCustomer
   ↓
DimBook
   ↓
DimAuthor
   ↓
DimShippingMethod
   ↓
DimStatus
   ↓
FactSales
   ↓
FactOrderStatus
```

---

## DimDate Package

Features:

* Script Component Generation
* Automated Calendar Creation
* Truncate-and-Load Strategy

(Insert DimDate Screenshot)

---

## DimCustomer Package

Features:

* SCD Type 2
* Historical Tracking
* Change Detection
* Automatic Versioning

(Insert DimCustomer Screenshot)

---

## DimBook Package

Features:

* Business Key Lookup
* Type 1 Updates

(Insert DimBook Screenshot)

---

## DimAuthor Package

Features:

* Author Dimension Population

(Insert DimAuthor Screenshot)

---

## BridgeBookAuthor Package

Features:

* Surrogate Key Resolution
* Many-to-Many Relationship Management

(Insert Bridge Screenshot)

---

## FactSales Package

Features:

* Multi-Dimension Lookups
* Revenue Calculations
* Surrogate Key Resolution

(Insert FactSales Screenshot)

---

## FactOrderStatus Package

Features:

* Accumulating Snapshot Design
* Order Lifecycle Tracking

(Insert FactOrderStatus Screenshot)

---

# Historical Data Management

The project implements Slowly Changing Dimension Type 2 for customer history tracking.

Tracked changes include:

* Customer Address Changes
* Location Changes

Implementation:

* StartDate
* EndDate
* IsCurrent

---

# OLAP Cube (SSAS)

## Dimensions

* Customer
* Book
* Author
* Date
* Shipping Method
* Status

## Measures

* Revenue
* Quantity Sold
* Order Count

## Calculated Metrics

* Average Order Value
* Revenue Growth
* Delivery Duration

(Add SSAS screenshots later)

---

# Power BI Dashboards

The reporting layer provides:

### Executive Dashboard

* Revenue KPIs
* Sales Trends
* Top Products

### Customer Analytics Dashboard

* Customer Distribution
* Geographic Analysis

### Operational Dashboard

* Shipping Performance
* Order Lifecycle Metrics

(Add Power BI screenshots later)

---

# Business Questions Answered

### Customer Perspective

* Who are the most valuable customers?
* Which cities generate the highest revenue?

### Product Perspective

* Which books perform best?
* Which authors generate the most revenue?

### Time Perspective

* What are seasonal sales patterns?
* How does revenue change year-over-year?

### Operations Perspective

* What is the average delivery time?
* Which shipping methods are most effective?

---

# Technologies Used

* SQL Server
* SSIS
* SSAS
* Power BI
* Dimensional Modeling
* Kimball Methodology

---

# Key Data Warehouse Concepts Demonstrated

* Star Schema Design
* Slowly Changing Dimensions (Type 2)
* Degenerate Dimensions
* Bridge Tables
* Accumulating Snapshot Facts
* ETL Orchestration
* OLAP Cubes
* Business Intelligence Reporting

---

# Future Enhancements

* Incremental Fact Loading
* Real-Time Data Pipelines
* Advanced DAX Measures
* Predictive Analytics
* Customer Segmentation Models

---

# README STRUCTURE

```text
/
├── docs/
│   ├── transactional_erd.png
│   ├── dimensional_model.png
│   ├── ssis/
│   ├── ssas/
│   └── dashboards/
│
├── ssis/
│   ├── 00_Master_ETL.dtsx
│   ├── 01_Load_DimDate.dtsx
│   ├── 02_Load_DimCustomer.dtsx
│   ├── 03_Load_DimBook.dtsx
│   ├── 04_Load_DimAuthor.dtsx
│   ├── 05_Load_DimShipping.dtsx
│   ├── 06_Load_DimStatus.dtsx
│   ├── 07_Load_FactSales.dtsx
│   └── 08_Load_FactOrderStatus.dtsx
│
├── ssas/
│   ├── cube_definition
│   └── dimensions
│
├── powerbi/
│   └── dashboard.pbix
│
└── README.md
```

---

# Author

**Hamid Mohamed Abdelhamid Hassan Elshaffei**

Data Engineer | Data Analyst | Business Intelligence Enthusiast

---
