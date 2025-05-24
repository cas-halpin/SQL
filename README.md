# 🛠️ Eamonn’s Hardware Database Proposal

**Author:** Cassidy Halpin  
**Date:** June 7, 2024  
**Course:** MIS445 – Database Systems  

##  Project Overview

Eamonn’s Hardware, a growing local tool rental and sales business, needed a scalable database system to replace its Excel-based recordkeeping. This proposal outlines the full database design and implementation—including entity relationship modeling (ERD), schema creation, data seeding, and query development—to support essential business operations.

## Goals of the Database

- **Tool Inventory:** Assign a unique store and manufacturer ID to each tool.
- **Tool Rentals:** Support up to 3 tools per customer rental.
- **Tool Categorization:** Categorize tools by manufacturer, supplier, power system, price, rental fee, insurance, etc.
- **Customer Management:** Track and grow customer data.
- **Manufacturer and Supplier Data:** Track relationships with tool sources.

##  Business Questions Answered

1. Which tools are currently rented out?
2. How many tools are rented by each customer?
3. What is the total rental income per customer?
4. Which tools are rented most frequently?
5. What is the average rental fee by category?
6. Which customers rented tools in the last month?
7. What were total earnings from rentals in the last month?
8. Which suppliers provide the most rented tools?
9. What is the distribution of tools by power system?
10. What is the total number of tools rented by category?

📄 _Full SQL queries provided in this repository._

##  Database Design

### Tables & Attributes

- **Customers:** CustID, First_Name, Last_Name, Street, City, Zip, Phone  
- **Tools:** ToolID, ManuID, Description, Power, Type, Price, RentFee, Insurance, SupplierID  
- **Rental_Transaction:** TransactionID, CustID, RentalDate, ReturnDate  
- **Rental_Details:** TransactionID, ToolID  
- **Supplier:** SupplierID, Name  
- **Manufactures:** ManuID, Name  
- **Purchases:** PurchaseID, SupplierID, ToolID, CustID, PurchaseDate, PurchaseTotal  

###  Relationships

- **One-to-Many:**  
  - Customers → Rental_Transaction  
  - Rental_Transaction → Rental_Details  
  - Tools → Rental_Details  
  - Purchases → Customers, Supplier, Tools  

- **Many-to-One:**  
  - Tools → Supplier  
  - Tools → Manufactures  

##  SQL Implementation

- **Table Creation Scripts:** Provided to define schema with appropriate data types (e.g., `DECIMAL(10,2)` for prices).
- **Seeding Scripts:** Includes INSERT statements for Customers, Manufacturers, Suppliers, Tools, Purchases, and Rentals.
- **Queries:** Designed to answer core business operations and reporting needs.

##  Lessons Learned

- Initially limited the rentals to one tool per transaction, which violated the requirement. Solved this by introducing a `Rental_Details` table to model many-to-many relationships.
- Encountered data type errors while running calculations on `VARCHAR` fields. This was resolved by changing monetary fields to `DECIMAL(10,2)` to accurately represent currency values.
- Gained insight into full-cycle database design—from client consultation and requirements gathering to implementation and testing.

##  Staffing and Implementation Considerations

- **System Administrator:** Required for performance monitoring and uptime.
- **Database Administrator:** Ensures data integrity, backups, and security.
- **Training:** Needed for employees and IT staff to adapt to the new system.
- **Migration:** Careful data migration from Excel with validation is essential to ensure consistency.

##  References

- IBM. (2021). *Data migration: Best practices, process & tools*. https://www.ibm.com/cloud/learn/data-migration  
- Mannino, M. V. (2023). *Database design, query formulation, and administration using Oracle and PostgreSQL*. SAGE.  
- Techopedia. (n.d.). *System administrator*. https://www.techopedia.com/definition/2983/system-administrator  

---

> This project demonstrates my ability to take a real-world client scenario, apply data modeling principles, and deliver a fully functioning SQL-based system aligned to business goals.
