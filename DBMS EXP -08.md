# Experiment No.08
### CREATE TABLE SALGRADE
~~~
CREATE TABLE SALGRADE(
GRADE CHAR(1),
LOSAL INT,
HISAL INT
);
INSERT INTO SALGRADE (GRADE, LOSAL, HISAL) VALUES
('A',700,1200),
('B',1201,1400),
('C',1401,2000),
('D',2001,3000),
('E',3001,9999);
~~~

### PROBLEM-01 Display all employees with their dept name.

~~~sql
SELECT E.ENAME, D.DNAME
FROM EMPLOYEE E
JOIN DEPARTMENT D
ON E.DEPTNO = D.DEPTNO;
~~~
### Output
~~~
+--------+------------+
| ENAME  | DNAME      |
+--------+------------+
| MILLER | RESEARCH   |
| SMITH  | ACCOUNTING |
| JONES  | ACCOUNTING |
| CLARK  | ACCOUNTING |
| KING   | ACCOUNTING |
| ADAMS  | ACCOUNTING |
| FORD   | ACCOUNTING |
| ALLEN  | SALES      |
| WARD   | SALES      |
| MARTIN | SALES      |
| BLAKE  | SALES      |
| TURNER | SALES      |
| JAMES  | SALES      |
| SCOTT  | OPERATIONS |
+--------+------------+
14 rows in set (0.001 sec)
~~~

### PROBLEM-02 Display those employees whose manager names is jones, and also display their manager name.

~~~sql
SELECT E.ENAME AS EMP_NAME, M.ENAME AS MANAGER_NAME
FROM EMPLOYEE E
JOIN EMPLOYEE M
ON E.MGR = M.EMPNO
WHERE M.ENAME = 'JONES';
~~~
### Output
~~~
+----------+--------------+
| EMP_NAME | MANAGER_NAME |
+----------+--------------+
| SCOTT    | JONES        |
| FORD     | JONES        |
+----------+--------------+
2 rows in set (0.001 sec)
~~~

### PROBLEM-03 Display employee name,his job,his,dept name,his manager name, his grade and make out of an under department wise.

~~~sql
SELECT E.ENAME, E.JOB, D.DNAME, M.ENAME AS MANAGER_NAME, S.GRADE
FROM EMPLOYEE E
JOIN DEPARTMENT D ON E.DEPTNO = D.DEPTNO
LEFT JOIN EMPLOYEE M ON E.MGR = M.EMPNO
JOIN SALGRADE S ON E.SAL BETWEEN S.LOSAL AND S.HISAL
ORDER BY D.DNAME;
~~~
### Output
~~~
+--------+-----------+------------+--------------+-------+
| ENAME  | JOB       | DNAME      | MANAGER_NAME | GRADE |
+--------+-----------+------------+--------------+-------+
| FORD   | ANALYST   | ACCOUNTING | JONES        | D     |
| ADAMS  | CLERK     | ACCOUNTING | SCOTT        | A     |
| JONES  | MANAGER   | ACCOUNTING | KING         | D     |
| KING   | PRESIDENT | ACCOUNTING | NULL         | E     |
| CLARK  | MANAGER   | ACCOUNTING | KING         | D     |
| SMITH  | CLERK     | ACCOUNTING | FORD         | A     |
| SCOTT  | ANALYST   | OPERATIONS | JONES        | D     |
| MILLER | CLERK     | RESEARCH   | CLARK        | B     |
| ALLEN  | SALESMAN  | SALES      | BLAKE        | C     |
| BLAKE  | MANAGER   | SALES      | KING         | D     |
| JAMES  | CLERK     | SALES      | BLAKE        | A     |
| TURNER | SALESMAN  | SALES      | BLAKE        | C     |
| WARD   | SALESMAN  | SALES      | BLAKE        | B     |
| MARTIN | SALESMAN  | SALES      | BLAKE        | B     |
+--------+-----------+------------+--------------+-------+
14 rows in set (0.002 sec)
~~~
