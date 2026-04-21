-- ============================================================
-- 📊 EMPLOYEE DATABASE ANALYSIS - COMPLETE SQL PROJECT
-- ============================================================

-- =========================
-- 1. CREATE DATABASE
-- =========================
CREATE DATABASE e;
USE e;

-- =========================
-- 2. CREATE TABLE
-- =========================
CREATE TABLE HR (
    Employee_ID INT PRIMARY KEY,
    Full_Name VARCHAR(100),
    Department VARCHAR(50),
    Salary_INR INT,
    Hire_Date DATE
);

-- =========================
-- 3. INSERT SAMPLE DATA
-- =========================
INSERT INTO HR VALUES
(1, 'Arun Kumar', 'HR', 60000, '2021-05-10'),
(2, 'Bala Singh', 'Finance', 120000, '2022-03-15'),
(3, 'Anita Sharma', 'IT', 700000, '2020-07-20'),
(4, 'Ravi Kumar', 'HR', 500000, '2023-01-01'),
(5, 'Suresh Babu', 'IT', 300000, '2022-06-18'),
(6, 'Priya Devi', 'Finance', 450000, '2021-09-25'),
(7, 'Anil Kumar', 'IT', 700000, '2023-02-11'),
(8, 'Kiran Raj', 'HR', 150000, '2022-11-05'),
(9, 'Deepa Nair', 'Finance', 800000, '2020-12-12'),
(10, 'Arun Kumar', 'HR', 60000, '2021-05-10'); -- duplicate

-- =========================
-- 4. VIEW DATA
-- =========================
SELECT * FROM HR;

-- =========================
-- 5. SELECT SPECIFIC COLUMNS
-- =========================
SELECT Employee_ID, Full_Name, Salary_INR FROM HR;

-- =========================
-- 6. FILTERING DATA
-- =========================

-- Salary > 50,000
SELECT Full_Name, Salary_INR 
FROM HR 
WHERE Salary_INR > 50000;

-- HR Department employees
SELECT Full_Name, Department 
FROM HR 
WHERE Department = 'HR';

-- =========================
-- 7. SORTING DATA
-- =========================
SELECT Full_Name, Salary_INR 
FROM HR 
ORDER BY Salary_INR DESC;

-- =========================
-- 8. AGGREGATE FUNCTIONS
-- =========================

SELECT COUNT(Full_Name) AS Total_Employees FROM HR;
SELECT SUM(Salary_INR) AS Total_Salary FROM HR;
SELECT MIN(Salary_INR) AS Min_Salary FROM HR;
SELECT MAX(Salary_INR) AS Max_Salary FROM HR;
SELECT AVG(Salary_INR) AS Avg_Salary FROM HR;

-- =========================
-- 9. DISTINCT VALUES
-- =========================
SELECT DISTINCT Department FROM HR;

-- =========================
-- 10. GROUP BY ANALYSIS
-- =========================

-- Total salary per department
SELECT Department, SUM(Salary_INR) AS Total_Salary
FROM HR
GROUP BY Department;

-- Employee count per department
SELECT Department, COUNT(*) AS Employee_Count
FROM HR
GROUP BY Department;

-- =========================
-- 11. PATTERN MATCHING
-- =========================
SELECT Full_Name 
FROM HR 
WHERE Full_Name LIKE 'A%';

-- =========================
-- 12. RANGE FILTERING
-- =========================
SELECT Full_Name, Salary_INR 
FROM HR 
WHERE Salary_INR BETWEEN 100000 AND 700000;

-- =========================
-- 13. CASE STATEMENT
-- =========================
SELECT Full_Name, Salary_INR,
CASE
    WHEN Salary_INR >= 700000 THEN 'High'
    WHEN Salary_INR >= 500000 THEN 'Medium'
    WHEN Salary_INR >= 100000 THEN 'Low'
    ELSE 'Very Low'
END AS Priority
FROM HR;

-- =========================
-- 14. TOP N RECORDS
-- =========================

-- Top 5
SELECT Full_Name, Salary_INR
FROM HR
ORDER BY Salary_INR DESC
LIMIT 5;

-- Top 2
SELECT Full_Name, Salary_INR
FROM HR
ORDER BY Salary_INR DESC
LIMIT 2;

-- =========================
-- 15. DATE FILTERING
-- =========================
SELECT Full_Name, Hire_Date
FROM HR
WHERE Hire_Date >= '2022-01-01';

-- =========================
-- 16. SUBQUERY
-- =========================

-- Above average salary
SELECT Full_Name, Salary_INR
FROM HR
WHERE Salary_INR > (SELECT AVG(Salary_INR) FROM HR);

-- =========================
-- 17. DUPLICATE DETECTION
-- =========================
SELECT Full_Name, COUNT(*) AS Duplicate_Count
FROM HR
GROUP BY Full_Name
HAVING COUNT(*) > 1;

-- =========================
-- 18. WINDOW FUNCTIONS
-- =========================

-- Dense Rank
SELECT Full_Name, Salary_INR,
DENSE_RANK() OVER (ORDER BY Salary_INR DESC) AS Rank_Position
FROM HR;

-- Running Total
SELECT Full_Name,
SUM(Salary_INR) OVER (ORDER BY Salary_INR DESC) AS Running_Total
FROM HR;

-- ============================================================
-- ✅ END OF COMPLETE SQL PROJECT
-- ============================================================

---

