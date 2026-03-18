# 📚 Book Store Data Analysis (PostgreSQL)

<p align="center">
  <b>SQL-Based Data Analysis Project</b><br>
  Exploring sales, customers, and inventory insights using PostgreSQL
</p>

<p align="center">
  <img src="https://img.shields.io/badge/PostgreSQL-Database-blue?logo=postgresql">
  <img src="https://img.shields.io/badge/SQL-Analysis-orange">
  <img src="https://img.shields.io/badge/Project-Type%3A%20Portfolio-green">
  <img src="https://img.shields.io/badge/License-MIT-lightgrey">
</p>

---

## 📖 Overview

This project demonstrates a complete **data analysis workflow using PostgreSQL** on a fictional bookstore database.  

It focuses on extracting meaningful business insights such as:
- 📈 Sales performance  
- 👥 Customer behavior  
- 📦 Inventory tracking  

---

## 🎯 Objectives

- Analyze book sales trends  
- Identify top-performing books and authors  
- Understand customer purchasing patterns  
- Monitor stock availability  

---

## 🗂️ Database Schema

The database consists of three relational tables:

### 📘 Books
| Column | Description |
|--------|------------|
| Book_ID | Primary Key |
| Title | Book name |
| Author | Author name |
| Genre | Category |
| Published_Year | Year published |
| Price | Book price |
| Stock | Available quantity |

---

### 👤 Customers
| Column | Description |
|--------|------------|
| Customer_ID | Primary Key |
| Name | Customer name |
| Email | Email address |
| Phone | Contact number |
| City | City |
| Country | Country |

---

### 🛒 Orders
| Column | Description |
|--------|------------|
| Order_ID | Primary Key |
| Customer_ID | Foreign Key |
| Book_ID | Foreign Key |
| Order_Date | Date of purchase |
| Quantity | Number of books |
| Total_Amount | Total price |

---

## ⚙️ Setup & Installation

1. Install PostgreSQL  
2. Open any SQL client (pgAdmin / DBeaver / psql)  
3. Run the SQL script:

```sql
-- Execute the provided SQL file to create tables and queries---

```

---

## 🚀 How to Use

1. Execute the SQL script to create the database schema (Books, Customers, Orders).
2. Populate the tables with sample data.
3. Run the analytical queries to explore insights related to sales, customers, and inventory.
4. Modify or extend queries to perform deeper analysis as needed.

---

## ✨ Key Features

- Well-structured relational database with proper foreign key constraints  
- 20+ real-world SQL queries for data analysis  
- Covers essential SQL operations:
  - Data filtering (`WHERE`)
  - Aggregations (`SUM`, `AVG`, `COUNT`)
  - Table joins (`INNER JOIN`, `LEFT JOIN`)
  - Grouping and conditions (`GROUP BY`, `HAVING`)
  - Sorting and limiting results (`ORDER BY`, `LIMIT`)  
- Designed for learning, practice, and portfolio demonstration  

---

## 📊 Analysis Highlights

### 📌 Sales Analysis
- Total revenue generated from all orders  
- Identification of most frequently ordered books  
- Genre-wise sales distribution  

### 👥 Customer Insights
- Customers with multiple purchases  
- Highest spending customer  
- Geographic distribution of high-value customers  

### 📦 Inventory Insights
- Total available stock  
- Books with lowest inventory levels  
- Remaining stock after fulfilling all orders  

---

## 💡 Example Queries

### 🔹 Total Revenue
```sql
SELECT SUM(total_amount) AS revenue FROM Orders;
```
### 🔹 Most Frequently Ordered Book
```sql
SELECT o.book_id, b.title, COUNT(o.order_id) AS order_count
FROM orders o
JOIN books b ON o.book_id = b.book_id
GROUP BY o.book_id, b.title
ORDER BY order_count DESC
LIMIT 1;
```
### 🔹 Remaining Stock After Orders
```sql
SELECT b.book_id, b.title, b.stock,
COALESCE(SUM(o.quantity), 0) AS ordered_quantity,
b.stock - COALESCE(SUM(o.quantity), 0) AS remaining_stock
FROM books b
LEFT JOIN orders o ON b.book_id = o.book_id
GROUP BY b.book_id;
```
---

### 🧠 Skills Demonstrated

- Strong SQL query writing and optimization
- Data analysis and interpretation
- Relational database design and normalization
- Business problem-solving using data
- Aggregation and reporting techniques

---

### 📦 Tools & Technologies

- PostgreSQL (Database Management System)
- SQL (Structured Query Language)

---

## 🛠️ Common Issues & Fixes

| Issue | Solution |
|------|----------|
| Tables already exist | Use `DROP TABLE IF EXISTS` before creating tables |
| Foreign key constraint errors | Insert data in correct order (Books → Customers → Orders) |
| NULL values in aggregations | Use `COALESCE()` to handle NULL results |
| Incorrect query output | Verify JOIN conditions and GROUP BY clauses |
| Date filtering issues | Ensure correct date format (`YYYY-MM-DD`) |

---

## 👤 Author

**YSamiksha Pawar**  
- GitHub: *https://github.com/samikshapawar08*  
- LinkedIn: *www.linkedin.com/in/samiksha-pawar-aa1018266*  

---

## 📜 License

This project is licensed under the **MIT License**.  
You are free to use, modify, and distribute this project with proper attribution.

---

## 🙏 Acknowledgement

This project was inspired by a YouTube tutorial.  
The implementation has been recreated and enhanced independently for learning and portfolio purposes.

---

## ⭐ Support

If you found this project helpful:

- ⭐ Star this repository  
- 🍴 Fork it for your own use  
- 📢 Share it with others  
