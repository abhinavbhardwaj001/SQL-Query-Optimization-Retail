# SQL Query Optimization & Performance Tuning (Virtual Retail System)

## 📌 Project Overview
This repository contains the SQL scripts, database schema setup, benchmark metrics, and optimization technical report for **Week 3: SQL Query Optimization and Performance Tuning**. 

The goal of this project is to analyze, refactor, and optimize high-volume transactional SQL queries within an enterprise retail database environment handling millions of records across customers, orders, inventory, and product categories.

---

## 🛠️ Key Performance Tuning Strategies Applied
- **Composite & Covering B-Tree Indexing:** Converted full table scans into Index-Only Scans, eliminating expensive bookmark/key lookups.
- **Sargability & Predicate Refactoring:** Eliminated scalar function wrappers (`YEAR()`, `MONTH()`, `CAST()`) around indexed filter columns to enable direct Index Range Seeks.
- **Join & Aggregation Optimization:** Replaced correlated scalar subqueries and implicit Cartesian joins with explicit ANSI INNER JOINs, Common Table Expressions (CTEs), and window functions.
- **Partition Pruning:** Implemented monthly range partitioning on dynamic transaction tables (`orders`, `order_items`) to prune non-matching storage segments during query execution.

---

## 📊 Before vs. After Optimization Benchmarks

| Scenario ID | Workload Scenario | Baseline Execution | Optimized Execution | Latency Reduction |
| :--- | :--- | :--- | :--- | :--- |
| **Scenario 1** | Date-Filtered Sales Aggregation | 4,850 ms | 180 ms | **96.3%** |
| **Scenario 2** | Multi-Store Inventory Lookup | 3,120 ms | 45 ms | **98.6%** |
| **Scenario 3** | Customer Lifetime Order History | 5,640 ms | 240 ms | **95.7%** |
| **Scenario 4** | Top-Selling Product Analysis | 7,290 ms | 410 ms | **94.4%** |

---

## 📂 Repository Structure
```text
├── schema.sql           # Database schema definition (Tables, Keys, Constraints)
├── baseline_queries.sql # Original unoptimized queries (Pre-optimization)
├── optimized_queries.sql# Refactored queries & DDL Indexing scripts (Post-optimization)
└── REPORT.md            # Detailed performance analysis report
