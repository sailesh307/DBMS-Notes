# Sub Queries
- Till Now we have learned that RDBMS tables are created on the basis of ER diagram and multiple tables are created in this process.
- But due to these multiple tables complete information may not be visible from a single table.
- For eg : in case of employee and department tables, [employee table will have only employee id and name but department table will have employee id, name, department id and department name.]


 Department ---🔶--- Employee
 ---
 1 to many relation

 Suppose we have a department table and employee table.

### Table `Department`

DCODE | DNAME | LOCATION
------|-------|--------
10 | Sales    | Delhi
20 | Marketing| Mumbai
30 | Production| Delhi
40 | Packing  | Rampur
80 | HR       | DLI
70 | IT       | Delhi

### Table `emp`

EMPCODE | NAME | CITY | MANAGER | DEPT
--------|------|------|---------|------
1 | Kumar | Delhi |  | 40
2 | Sumit | Kanpur | 1 | 
3 | Rohit | DDN | 2 | 10
4 | akash | goa | 1 
5 | akhil | goa | 2 | 30
6 | tarun | bombay | 3 | 10
25 | Mohan | DDN | 4 | 20
26 | Rohit | Mrt | 5
27 | ABC | Merut | 1 | 30
39 | abc | xyz | 1 | 40
7 | amit | rampur | 6 | 30

Why there are two tables?
> Beacuse of the one to many relation, if there is only one table then data will be repeated many time.

**Ques 1:** Display empcode, name of those employees who are not from any department.
```
SELECT empcode, name FROM emp WHERE dept IS NULL;
```
OUTPUT:

EMPCODE | NAME
--------|------
2 | Sumit
4 | akash
26 | Rohit

**Ques 2:** Display empcode, name of those employees with department code as 40.
```
SELECT empcode, name FROM emp WHERE dept = 40;
```
OUTPUT:

EMPCODE | NAME
--------|------
1 | Kumar
39 | abc


# Start of Sub Queries

**Ques 3:** Display details of those employees who are working in `sales` department.
```
SELECT * FROM emp WHERE dept IN (SELECT dcode FROM dept WHERE dname = 'Sales');
```
OUTPUT:

EMPCODE | NAME | CITY | MANAGER | DEPT
--------|------|------|---------|------
6 | tarun | bombay | 3 | 10
3 | Rohit | DDN | 2 | 10

> - in above query, we are using sub query to get the department code of sales department. 
>
>- then we are simply using `IN ()` 
>- in brack all `DCODE` of sales department will come
>
>- if there are two `DCODE` of sales the it will be `IN (10, 15)` and all details will be displayed. for these two `DCODE`

**NOTE : `IN ()` is very important**


NOW Suppose we have one more 

### table `Project`

PCODE | PNAME | BUDGET | PMANAGER
------|-------|--------|--------
111 | Pepsico | 650000 | 25
222 | Patanjali | 88900 | 3
333 | ITC | 4555 | 27

- PRIMARY KEY : EMPCODE OF `emp` table
- FOREIGN KEY : PMANAGER OF `Project` table


**Ques 4:** Display the budget of all projects.
```
SELECT budget FROM project;
```
OUTPUT:

BUDGET|
------|
650000|
88900|
4555|

**Ques 5:** Display the MAX budget
```
SELECT MAX(budget) FROM project;
```
OUTPUT:

MAX(BUDGET)|
----------|
650000|

**Ques 6:** Display the 2nd most expensive project.
```
SELECT MAX(budget) FROM project WHERE budget NOT IN (SELECT MAX(budget) FROM project);
```
OUTPUT:

MAX(BUDGET)|
----------|
88900|

**Ques 7:** Display the details of project with dname=marketing.

if we see there is no direct link b/w project budget and the dname of department then we can use sub query.

**Process of sub query will be :**

[project](#table-project) => [emp](#table-emp) => [department](#table-department) 

```
SELECT budget FROM project
   WHERE pmanager IN (
       SELECT empcode FROM emp WHERE dept IN (
           SELECT dcode FROM department WHERE dname = 'Marketing'
       )
   )
);
```
OUTPUT:

DCODE |
------|
20 |
