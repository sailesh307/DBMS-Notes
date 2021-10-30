# Normal Form
- Normalization is the process of organizing the data in the database.
- Normalization is used to minimize the redundancy from a relation or set of relations. 
- It is also used to eliminate the undesirable characteristics like Insertion, Update and Deletion Anomalies.
- Normalization divides the larger table into the smaller table and links them using relationship.
- The normal form is used to reduce redundancy from the database table

**IN SIMPLE WORDS :** breaking of a large table into smaller tables is called normalization

**It should follow following 2 rules:**
- Lossless join property [there should not be any data loss]
- Dependency preservation property [relationship should not be change]

EXAMPLES:

Suppose there is a table combination of emp and dept

EMPCODE | NAME  | CITY  | MANAGER | DEPT | DCODE | DNAME      | LOCATION
--------|-------|-------|---------|------|-------|------------|---------
 1      | Kumar |Delhi  |         | 40   | 40    | Packing    | Rampur
 3      | Rohit |DDN    | 2       | 10   | 10    | Sales      | Delhi
 5      | akhil |goa    | 2       | 30   | 30    | Production | Delhi
 6      | tarun |bombay | 3       | 10   | 10    | Sales      | Delhi
25      | Mohan |DDN    | 4       | 20   | 20    | Marketing  | Mumbai
27      | ABC   |Merut  | 1       | 30   | 30    | Production | Delhi
39      | abc   |xyz    | 1       | 40   | 40    | Packing    | Rampur
 7      | amit  |rampur | 6       | 30   | 30    | Production | Delhi


Why not single table?

- Because as we can see it has number of anomalies
- Eg: Whenever employee `dcode` is `30`, its `dname` `'production'` is repeated [redundancy]
- by seeing this table we can exactly tell the no. of deapartment if we make two table `emp` for basic details of employee and `dept` for department details and this will be more readable.

---

NORMAL FORM:
- are Functional Dependencies based conditions satisfied by relations(tables)
    - 1NF
    - 2NF
    - 3NF
- Normalization is the process of breaking a bigger relation (table) which has many anomolies into smaller relations (tables) free from anomalies.

## 1NF (1st Normal Form)
- A table is said to be in 1NF if it satisfies two conditions:
    - All the columns are atomic 
    - There are np repeating groups (multiple values)
- Eg: **Is the following table in 1NF?**

ROLLNO | NAME    | CITY |PHONE
-------|---------|------|------
1      | Amit Kr | DDN  | 313,418,316
2      | Rohit   | DDN  | 821,388
3      | Mohit Kr Sharma | HRD | 3168

**ANSWER :** 
- No , the above table is not in 1 NF because the column `NAME` is not atomic, it can be broken into `firstName` , `middleName` and `lastName`. 
- Also the column `PHONE` contains multiple values in a single row [seprated by commas]. 

**SOLUTION:**

ROLLNO | FNAME | MNAME | LNAME | CITY |PH1 | PH2 | PH3
-------|-------|-------|-------|------|----|-----|----
1      | Amit  |Kr     |       | DDN  |313 |418  |316
2      | Rohit |       |       | DDN  |821 |388
3      | Mohit |Kr     |Sharma | HRD  |3168

NOW it is in 1NF

## 2NF (2nd Normal Form)
- It is related to the concept of full functional dependency.
- A table is said to be in 2NF if it does not have any partial FD (i.e all non-prime attributes are completely dependent on entire primary key & not on any part of primary key[it happen when primary key is made up of more than one column])
- this is in case of composite key[key made up of more than one column]

OrderNo | ItemNO | ItemName | Qty 
-------|--------|---------|----
101 | 11 | Pepsi | 7
101 | 22 | Colgate | 6
101 | 33 | Tide |3 
102 | 33 | Tide | 7
103 | 11 | Pepsi | 5

In this table Composite Key is (`OrderNo`, `ItemNO`)

and `ItemName` , `Qty` are non-prime attributes

FDs are :

F :

- OrderNo, ItemNO -> ItemName
- OrderNo, ItemNO -> Qty

But there is one more FD
- ItemNo -> ItemName

This is partial FD

IteamNO is prime but not primary Key & ItemName is non-prime attribute

So above table is not in 2NF

Due to partial FD their is redundancy anomoly

**SOLUTION :**
- Identify partial FD `X` -> `Y`
- Remove `Y` from original table
- Create a new table `XY` with `X` as primary key.

Final Two tables are:

Table 1

OrderNo | ItemNO |Qty 
--------|--------|----
101     | 11     | 7
101     | 22     | 6
101     | 33     | 3 
102     | 33     | 7
103     | 11     | 5

Table 2

ItemNo | ItemName
-------|-----------
11     | Pepsi
22     | Colgate
33     | Tide
44     | Deo
55     | Lux


## 3NF (3rd Normal Form)
- It is related to the concept of transitive Functional Dependencies (FDs).
- A table is said to be in 3NF if it does not have FD of the form
    - X -> Y and Y -> Z , then Z -> X

ROLLNO | NAME    | YEAR | HOSTEL
-------|---------|------|--------
1      | A       | 1    | Ganga
2      | B       | 1    | Ganga
3      | C       | 2    | Yamuna
4      | A       | 3    | Kaveri
5      | D       | 2    | Yamuna
6      | B       | 1    | Ganga

> here `ROLLNO` is Prime
> and other columns are non prime

The above table is not in 3NF beacuse
in the tabke 
* `ROLLNO` -> `YEAR`
* `YEAR` -> `HOSTEL`
* ∴ `ROLLNO` -> `HOSTEL`

**SOLUTION:**

NP = non-prime
FD = functional dependency

**Step 1:** Take the non-prime FDs as X->Y <br>
$~~~~~~~~~~$ `YEAR` -> `HOSTEL`<br>
$~~~~~~~~~~$ `X` -> `Y`

**Step 2:** Remove `Y` (`HOSTEL`) from original table

**Step 3:** Create a new table `XY` with X as Primary Key

**Step 4:** Now our original table is normalized or decomposed into following two tables:

**Table 1**

ROLLNO | NAME    | YEAR 
-------|---------|------
1      | A       | 1    
2      | B       | 1    
3      | C       | 2    
4      | A       | 3    
5      | D       | 2    
6      | B       | 1    

`ROLLNO` is primary key in table 1

**Table 2**

YEAR | HOSTEL
-----|--------
1    | Ganga
2    | Yamuna
3    | Kaveri
4    | Saraswati

`YEAR` is primary key in 2nd table

NOW two tables are normalized