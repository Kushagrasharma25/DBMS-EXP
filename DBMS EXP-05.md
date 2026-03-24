# <center>Experiment No.5
### Problem 1: Display the Total Number of Employee Working in the Company

```sql
SELECT COUNT(*) AS TOTAL_EMPLOYEES
FROM EMPLOYEE;
```

**Output:**
```
+-----------------+
| TOTAL_EMPLOYEES |
+-----------------+
|              14 |
+-----------------+
1 row in set (0.001 sec)
```

---

### Problem 2: Display the Total Salary Being Paid to All Employees

```sql
SELECT SUM(SAL) AS TOTAL_SALARY
FROM EMPLOYEE;
```

**Output:**
```
+--------------+
| TOTAL_SALARY |
+--------------+
|        29025 |
+--------------+
1 row in set (0.001 sec)
```

---

### Problem 3: Display the Maximum Salary from Employee Table

```sql
SELECT MAX(SAL) AS MAX_SALARY
FROM EMPLOYEE;
```

**Output:**
```
+------------+
| MAX_SALARY |
+------------+
|       5000 |
+------------+
1 row in set (0.001 sec)
```

---

### Problem 4: Display the Minimum Salary from Employee Table

```sql
SELECT MIN(SAL) AS MIN_SALARY
FROM EMPLOYEE;
```

**Output:**
```
+------------+
| MIN_SALARY |
+------------+
|        800 |
+------------+
1 row in set (0.001 sec)
```

---

### Problem 5: Display the Average Salary from Employee Table

```sql
SELECT AVG(SAL) AS AVG_SALARY
FROM EMPLOYEE;
```

**Output:**
```
+-------------+
| AVG_SALARY  |
+-------------+
| 2073.214286 |
+-------------+
1 row in set (0.001 sec)
```

---

### Problem 6: Display the Maximum Salary Being Paid to Clerk

```sql
SELECT MAX(SAL) AS MAX_CLERK_SALARY
FROM EMPLOYEE
WHERE JOB = 'CLERK';
```

**Output:**
```
+------------------+
| MAX_CLERK_SALARY |
+------------------+
|             1300 |
+------------------+
1 row in set (0.001 sec)
```

---

### Problem 7: Display the Maximum Salary Being Paid in Dept No 20

```sql
SELECT MAX(SAL) AS MAX_SAL_DEPT20
FROM EMPLOYEE
WHERE DEPTNO = 20;
```

**Output:**
```
+----------------+
| MAX_SAL_DEPT20 |
+----------------+
|           5000 |
+----------------+
1 row in set (0.001 sec)
```


---

### Problem 8: Display the Minimum Salary Paid to Any Salesman

```sql
SELECT MIN(SAL) AS MIN_SALESMAN_SALARY
FROM EMPLOYEE
WHERE JOB = 'SALESMAN';
```

**Output:**
```
+---------------------+
| MIN_SALESMAN_SALARY |
+---------------------+
|                1250 |
+---------------------+
1 row in set (0.001 sec)
```

---

### Problem 9: Display the Average Salary Drawn by Managers

```sql
SELECT AVG(SAL) AS AVG_MANAGER_SALARY
FROM EMPLOYEE
WHERE JOB = 'MANAGER';
```

**Output:**
```
+--------------------+
| AVG_MANAGER_SALARY |
+--------------------+
|        2758.333333 |
+--------------------+
1 row in set (0.001 sec)
```

---

### Problem 10: Display the Total Salary Drawn by Analyst Working in Dept No 40

```sql
SELECT SUM(SAL) AS TOTAL_ANALYST_SAL_DEPT40
FROM EMPLOYEE
WHERE JOB = 'ANALYST'
  AND DEPTNO = 40;
```

**Output:**
```
+--------------------------+
| TOTAL_ANALYST_SAL_DEPT40 |
+--------------------------+
|                     3000 |
+--------------------------+
1 row in set (0.001 sec)
```

---

### Problem 11: Display the Names of the Employee in Uppercase

```sql
SELECT UPPER(ENAME) AS EMPLOYEE_NAME_UPPER
FROM EMPLOYEE;
```

**Output:**
```
+---------------------+
| EMPLOYEE_NAME_UPPER |
+---------------------+
| SMITH               |
| ALLEN               |
| WARD                |
| JONES               |
| MARTIN              |
| BLAKE               |
| CLARK               |
| SCOTT               |
| KING                |
| TURNER              |
| ADAMS               |
| JAMES               |
| FORD                |
| MILLER              |
+---------------------+
14 rows in set (0.001 sec)
```

---

### Problem 12: Display the Names of the Employee in Lowercase

```sql
SELECT LOWER(ENAME) AS EMPLOYEE_NAME_LOWER
FROM EMPLOYEE;
```

**Output:**
```
+---------------------+
| EMPLOYEE_NAME_LOWER |
+---------------------+
| smith               |
| allen               |
| ward                |
| jones               |
| martin              |
| blake               |
| clark               |
| scott               |
| king                |
| turner              |
| adams               |
| james               |
| ford                |
| miller              |
+---------------------+
14 rows in set (0.001 sec)
```

---

### Problem 13: Display the Names of the Employee in Proper Case

```sql
SELECT CONCAT(UPPER(SUBSTRING(ENAME, 1, 1)), LOWER(SUBSTRING(ENAME, 2))) AS EMPLOYEE_NAME_PROPER
FROM EMPLOYEE;
```

**Output:**
```
+----------------------+
| EMPLOYEE_NAME_PROPER |
+----------------------+
| Smith                |
| Allen                |
| Ward                 |
| Jones                |
| Martin               |
| Blake                |
| Clark                |
| Scott                |
| King                 |
| Turner               |
| Adams                |
| James                |
| Ford                 |
| Miller               |
+----------------------+
14 rows in set (0.001 sec)
```

---

### Problem 14: Display the Length of Your Name Using Appropriate Function

```sql
SELECT LENGTH('shreyansh pratap mishra') AS NAME_LENGTH;
```

**Output:**
```
+-------------+
| NAME_LENGTH |
+-------------+
|          10 |
+-------------+
1 row in set (0.001 sec)
```

---

### Problem 15: Display the Length of All the Employee Names

```sql
SELECT ENAME, LENGTH(ENAME) AS NAME_LENGTH
FROM EMPLOYEE;
```

**Output:**
```
+--------+-------------+
| ENAME  | NAME_LENGTH |
+--------+-------------+
| SMITH  |           5 |
| ALLEN  |           5 |
| WARD   |           4 |
| JONES  |           5 |
| MARTIN |           6 |
| BLAKE  |           5 |
| CLARK  |           5 |
| SCOTT  |           5 |
| KING   |           4 |
| TURNER |           6 |
| ADAMS  |           5 |
| JAMES  |           5 |
| FORD   |           4 |
| MILLER |           6 |
+--------+-------------+
14 rows in set (0.001 sec)
```
