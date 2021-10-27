# Primary Key
- whose data is `unique` + `non-null`
- It can be created at column and row/table level
- table can have only 1 Primary Key
- It can be made up of more than one column(composite Primary key)
---
**There are two types :**
- **Atomic Primary Key** : Single column
- **Composite Primary Key** : Multiple column (or more than one)

## 1. Atomic Primary Key
synatx : 
```
CREATE TABLE student
(
    roll_no number PRIMARY KEY,
    name varchar2(20),
    marks number
);
```

## 2. Composite Primary Key
syntax:
```
CREATE TABLE student
(
    roll_no number,
    student_id number,
    name varchar(220),
    PRIMARY KEY(roll_no, student_id)
);
```
> here column `roll_no` and column `student_id` is called `prime column`

> and `roll_no` and `student_id` combined are called `primary Key`

real Life example :
- multiple users travelling with same ticket in train

eg:

Primary Key = (roll_no, student_id)
ROLL_NO | STUDENT_ID | NAME
--- | --- | ---
1   | 101 | amit
2   | 102 | anil
2   | 103 | anuj

`(2, 102, anil)` and `(2, 103, anuj)` is valid
`(2, 102, anil)` and `(3, 102, anuj)` is valid
`(2, 102, anil)` and `(2, 102, anuj)` is in-valid beacuse `roll_no` and `student_id` combined can't be same but indivisually can be same

---

## Column level
eg : 
```
CREATE TABLE student
(
    roll_no number PRIMARY KEY,
    name varchar(20)
);
```

## Row/Table Level
eg : 
```
CREATE TABLE student
(
    roll_no number,
    name varchar(20),
    PRIMARY KEY(roll_no)
);
```

## Removing Primary Key
```
ALTER TABLE table_name DROP PRIMARY KEY;
```
> we can't remove `primary key` if it parent of other foregin key

> to remove primary key 1st remove all references of primary key 

## Adding Primary Key
```
ALTER TABLE table_name ADD PRIMARY KEY(column_name)
```
Conditions for adding Primary Key
- that column values sould be `unique` and `non-null` 
