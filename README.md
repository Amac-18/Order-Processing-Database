# Dropshipping-sql-database

## Overview
Designed and implemented a 12-table relational SQL database to support the backend structure of my e-commerce business. The system models customers, orders, products, suppliers, platforms, and addresses while enforcing relational integrity using primary keys, foreign keys, composite keys, and bridge tables for many-to-many relationships.

Notes: This is a beginner-level database design project to practice entity-relationship modeling, bridge tables, and subtypes. It was created as part of learning SQL, database normalization, and schema design.

## Database Design

### Core Entities 
- Customer
- Address
- Orders
- Supplier
- Product
- Platform
## Bridge Entities
- Customer_Address
- Supplier_Platform
- Supplier_Product
- Order_Detail

# Database Schema Overview

## Customer and Address
Customer(Customer_ID (PK), F_Name, L_Name)
Address(Address_ID (PK), Address_Type, Street_Name, Street_Number, Unit_Number (Null), City, Country)
   ├─ US_Address(Address_ID (PK/FK), State, Zip_Code)
   └─ International_Address(Address_ID (PK/FK), Province_Region, Postal_Code)

Customer_Address(Customer_ID (PK/FK), Address_ID (PK/FK))   
# Bridge table for M:N Customer ↔ Address

## Supplier and Platform
Supplier(Supplier_ID (PK), Supplier_Name, Supplier_Email)
Platform(Platform_ID (PK), Platform_Name)
Supplier_Platform(Supplier_ID (PK/FK), Platform_ID (PK/FK))  
# Bridge table for M:N Supplier ↔ Platform

## Product and Supplier
Product(Product_ID (PK), Product_Type_ID (FK), Product_Name, Product_Description, Base_Price, Selling_Price)
Product_Type(Product_Type_ID (PK), Product_Category)
Supplier_Product(Supplier_ID (PK/FK), Product_ID (PK/FK))   
# Bridge table for M:N Supplier ↔ Product

## Orders and Order Details
Orders(Order_ID (PK), Customer_ID (FK), Address_ID (FK), Order_Date, Total_Amount)
Order_Detail(Order_ID (PK/FK), Product_ID (PK/FK), Quantity, Unit_Price)  
# Bridge table for M:N Orders ↔ Product
  
  
  
