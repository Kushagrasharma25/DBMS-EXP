# Experiment No.3
### CREATE TABLE SALGRADE
~~~
CREATE TABLE SALGRADE(
GRADE CHAR(1),
LOSAL INT,
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
