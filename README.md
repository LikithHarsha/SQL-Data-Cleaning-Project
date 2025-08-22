# 🧹 SQL Data Cleaning – World Layoffs Dataset  

## 📌 Project Overview  
This project focuses on **cleaning and preprocessing** a dataset related to global layoffs using **SQL**.  
The raw dataset contained duplicates, inconsistent formatting, null values, and unnecessary rows.  

Through a series of SQL queries, the dataset was transformed into a **clean, reliable, and analysis-ready table**.  

---

## 🔹 Data Cleaning Steps  

### 1. Data Staging  
- Created a staging table (`layoffs_staging`) to preserve the raw dataset.  
- Inserted all data into the staging table for cleaning operations.  

### 2. Removing Duplicates  
- Used **window functions** (`ROW_NUMBER() OVER (PARTITION BY ...)`) with CTEs to identify duplicate rows.  
- Deleted duplicate entries while keeping the first occurrence.  

### 3. Standardizing Data  
- **Trimmed extra spaces** in `company` names.  
- Standardized **industry names** (e.g., “Crypto%” → “Crypto”).  
- Cleaned **country names** by removing trailing characters (e.g., "United States.").  
- Converted `date` column from text to proper **DATE** format using `STR_TO_DATE`.  

### 4. Handling Null & Blank Values  
- Converted blank `industry` fields into NULL.  
- Used **self-joins** to fill missing industry values from other records of the same company.  
- Removed rows where both `total_laid_off` and `percentage_laid_off` were NULL (meaningless data).  

### 5. Final Touches  
- Dropped the helper column (`row_num`) used for duplicate detection.  
- Ensured the final table (`layoffs_staging2`) was **clean and consistent**.  

---

## 🔹 SQL Concepts Used  

- **CTEs (Common Table Expressions)**  
- **Window Functions** (`ROW_NUMBER`)  
- **String Functions** (`TRIM`, `REPLACE`, `UPPER/LOWER`)  
- **Date Conversion** (`STR_TO_DATE`)  
- **Joins** (self-join to populate missing values)  
- **Conditional Updates & Deletes**  

---

## 📂 Repository Structure  

