# <center>Experiment No.4
### Problem 1: Display Employees Who Joined Before 30th June 80 or After 31st Dec 81

```sql
SELECT *
FROM EMPLOYEE
WHERE HIREDATE < '1980-06-30'
   OR HIREDATE > '1981-12-31';
```

**Corrected Output:**
```
+-------+--------+---------+------+------------+------+------+--------+
| EMPNO | ENAME  | JOB     | MGR  | HIREDATE   | SAL  | COMM | DEPTNO |
+-------+--------+---------+------+------------+------+------+--------+
|  7788 | SCOTT  | ANALYST | 7566 | 1982-12-09 | 3000 | NULL |     40 |
|  7876 | ADAMS  | CLERK   | 7788 | 1983-01-12 | 1100 | NULL |     20 |
|  7934 | MILLER | CLERK   | 7782 | 1982-01-23 | 1300 | NULL |     10 |
+-------+--------+---------+------+------------+------+------+--------+
3 rows in set (0.001 sec)
```

---

### Problem 2: Display Employees Whose Names Have Second Alphabet A

```sql
SELECT ENAME
FROM EMPLOYEE
WHERE ENAME LIKE '_A%';
```

**Output:**
```
+--------+
| ENAME  |
+--------+
| WARD   |
| MARTIN |
| JAMES  |
+--------+
3 rows in set (0.001 sec)
```


---

### Problem 3: Display Employees Whose Name Is Exactly Five Characters in Length

```sql
SELECT ENAME
FROM EMPLOYEE
WHERE LENGTH(ENAME) = 5;
```

**Output:**
```
+-------+
| ENAME |
+-------+
| SMITH |
| ALLEN |
| JONES |
| BLAKE |
| CLARK |
| SCOTT |
| ADAMS |
| JAMES |
+-------+
8 rows in set (0.001 sec)
```


---

### Problem 4: Display the Name of the Employees Whose Name Have Second Last Letter is A

```sql
SELECT ENAME
FROM EMPLOYEE
WHERE ENAME LIKE '%A_';
```

**Explanation:** The pattern `%A_` means:
- `%` = any sequence of characters (including empty)
- `A` = the letter 'A' at the second last position
- `_` = exactly one character (the last character)

**Output:**
```
+--------+
| ENAME  |
+--------+
| BLAKE  |
| ADAMS  |
+--------+
2 rows in set (0.001 sec)
```

---

### Problem 5: Display Employees Who Are Not Working as Salesman or Clerk or Analyst

```sql
SELECT ENAME, JOB
FROM EMPLOYEE
WHERE JOB NOT IN ('SALESMAN', 'CLERK', 'ANALYST');
```

**Output:**
```
+-------+-----------+
| ENAME | JOB       |
+-------+-----------+
| JONES | MANAGER   |
| BLAKE | MANAGER   |
| CLARK | MANAGER   |
| KING  | PRESIDENT |
+-------+-----------+
4 rows in set (0.001 sec)
```

---

### Problem 6: Display Employee Name Along with Annual Salary (sal*12), Highest Salary First

```sql
SELECT ENAME, SAL * 12 AS ANNUAL_SALARY
FROM EMPLOYEE
ORDER BY ANNUAL_SALARY DESC;
```

**Output:**
```
+--------+---------------+
| ENAME  | ANNUAL_SALARY |
+--------+---------------+
| KING   |         60000 |
| SCOTT  |         36000 |
| FORD   |         36000 |
| JONES  |         35700 |
| BLAKE  |         34200 |
| CLARK  |         29400 |
| ALLEN  |         19200 |
| TURNER |         18000 |
| MILLER |         15600 |
| WARD   |         15000 |
| MARTIN |         15000 |
| ADAMS  |         13200 |
| JAMES  |         11400 |
| SMITH  |          9600 |
+--------+---------------+
14 rows in set (0.001 sec)
```


---

### Problem 7: Display Name, Sal, HRA, PF, DA, TotalSal for Each Employee

```sql
SELECT ENAME,
       SAL,
       SAL * 0.15 AS HRA,
       SAL * 0.05 AS PF,
       SAL * 0.10 AS DA,
       (SAL + SAL * 0.15 + SAL * 0.10) - SAL * 0.05 AS TOTALSAL
FROM EMPLOYEE;
```

**Output:**
```
+--------+------+---------+---------+---------+----------+
| ENAME  | SAL  | HRA     | PF      | DA      | TOTALSAL |
+--------+------+---------+---------+---------+----------+
| SMITH  |  800 | 120.00  |  40.00  |  80.00  |   960.00 |
| ALLEN  | 1600 | 240.00  |  80.00  | 160.00  |  1920.00 |
| WARD   | 1250 | 187.50  |  62.50  | 125.00  |  1500.00 |
| JONES  | 2975 | 446.25  | 148.75  | 297.50  |  3570.00 |
| MARTIN | 1250 | 187.50  |  62.50  | 125.00  |  1500.00 |
| BLAKE  | 2850 | 427.50  | 142.50  | 285.00  |  3420.00 |
| CLARK  | 2450 | 367.50  | 122.50  | 245.00  |  2940.00 |
| SCOTT  | 3000 | 450.00  | 150.00  | 300.00  |  3600.00 |
| KING   | 5000 | 750.00  | 250.00  | 500.00  |  6000.00 |
| TURNER | 1500 | 225.00  |  75.00  | 150.00  |  1800.00 |
| ADAMS  | 1100 | 165.00  |  55.00  | 110.00  |  1320.00 |
| JAMES  |  950 | 142.50  |  47.50  |  95.00  |  1140.00 |
| FORD   | 3000 | 450.00  | 150.00  | 300.00  |  3600.00 |
| MILLER | 1300 | 195.00  |  65.00  | 130.00  |  1560.00 |
+--------+------+---------+---------+---------+----------+
14 rows in set (0.001 sec)
```

---

### Problem 8: Update Salary by 10% for Employees Not Eligible for Commission

```sql
UPDATE EMPLOYEE
SET SAL = SAL * 1.10
WHERE COMM IS NULL;
```

**Output:**
```
Query OK, 9 rows affected (0.003 sec)
Rows matched: 9  Changed: 9  Warnings: 0
```

**Verification:**
```sql
SELECT ENAME, SAL, COMM
FROM EMPLOYEE
WHERE COMM IS NULL;
```

```
+--------+---------+------+
| ENAME  | SAL     | COMM |
+--------+---------+------+
| SMITH  |  880.00 | NULL |
| JONES  | 3272.50 | NULL |
| BLAKE  | 3135.00 | NULL |
| CLARK  | 2695.00 | NULL |
| SCOTT  | 3300.00 | NULL |
| KING   | 5500.00 | NULL |
| ADAMS  | 1210.00 | NULL |
| JAMES  | 1045.00 | NULL |
| FORD   | 3300.00 | NULL |
| MILLER | 1430.00 | NULL |
+--------+---------+------+
10 rows in set (0.001 sec)
```

---

### Problem 9: Display Employees Whose Salary Is More Than 3000 After 20% Increment

```sql
SELECT ENAME, SAL, SAL * 1.20 AS SAL_AFTER_INCREMENT
FROM EMPLOYEE
WHERE SAL * 1.20 > 3000;
```

**Output:**
```
+-------+------+---------------------+
| ENAME | SAL  | SAL_AFTER_INCREMENT |
+-------+------+---------------------+
| JONES | 2975 |             3570.00 |
| BLAKE | 2850 |             3420.00 |
| SCOTT | 3000 |             3600.00 |
| KING  | 5000 |             6000.00 |
| FORD  | 3000 |             3600.00 |
+-------+------+---------------------+
5 rows in set (0.001 sec)
```

---

### Problem 10: Display Employees Whose Salary Contains At Least 3 Digits

```sql
SELECT ENAME, SAL
FROM EMPLOYEE
WHERE SAL >= 100;
```

**Alternative using LENGTH:**
```sql
SELECT ENAME, SAL
FROM EMPLOYEE
WHERE LENGTH(CAST(SAL AS UNSIGNED)) >= 3;
```

**Output:**
```
+--------+------+
| ENAME  | SAL  |
+--------+------+
| SMITH  |  800 |
| ALLEN  | 1600 |
| WARD   | 1250 |
| JONES  | 2975 |
| MARTIN | 1250 |
| BLAKE  | 2850 |
| CLARK  | 2450 |
| SCOTT  | 3000 |
| KING   | 5000 |
| TURNER | 1500 |
| ADAMS  | 1100 |
| JAMES  |  950 |
| FORD   | 3000 |
| MILLER | 1300 |
+--------+------+
14 rows in set (0.001 sec)
```
