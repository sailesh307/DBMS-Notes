# GROUP BY

table `course`

CODE | COURSE_NAME | FEES | SEMESTER | DEPT
---- | ----------- | ---- | -------- | ----
101  | MCA         | 80000| 6        | MCA
102  | MBA         | 50000| 4        | MGMIT
103  | Btech       | 45000| 8        | ENGG
104  | BCA         | 45000| 6        | MCA
105  | BSCIT       | 25000| 6        | ALLIED
106  | BSCIT       | 35000| 6        | ALLIED
107  | BBA         | 35000| 6        | MGMT
108  | OCP         |  3000| 2        | MCA
109  | PGDM        | 25000| 3        | MGMT
110  | CCNA        | 15000| 3        | ENGG


**Ques 1 :** Display all course fees
```
SELECT FEES FROM course;
```
OUTPUT : 

FEES|
----|
80000|
50000|
45000|
45000|
25000|
35000|
35000|
3000|
25000|
15000|

**Ques 2 :** Display sum of all course fees
```
SELECT SUM(fees) FROM course;
```
OUTPUT :

SUM(FEES)|
--------|
358000|


**Ques 3 :** Display Department wise sum of course fees.
```
SELECT dept, SUM(fees) FROM course GROUP BY dept;
```
OUTPUT :

DEPT   | SUM(FEES)|
-------| --------|
ENGG   | 60000
MCA    | 128000
ALLIED | 60000
MGMT   | 110000

**NOTE :** we can only use `GROUP BY` with those columns or expression with which we can make groups.

Following are two things:
- functions (SUM, AVG, MIN, MAX, COUNT, etc)
- grouping columns [columns on which we can make groups]


# HAVING

**Ques 4 :** Display Department wise sum of course feeshaving sum of course fees > 100000.
```
SELECT dept, SUM(fees) FROM course GROUP BY dept HAVING SUM(fees) > 100000;
```
OUTPUT :

DEPT | SUM(FEES)|
-----| --------|
MCA  | 128000
MGMT | 110000


## DIFFERENCE BETWEEN `WHERE` AND `HAVING` :

WHERE | HAVING
------|--------
It is used while reading data if condition <br> not satisfied then data is not read. | It is used while writing data if condition <br> not satisfied then data is not written.

