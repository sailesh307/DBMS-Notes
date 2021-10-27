# Data Dictionary tables
- these are present in system but we can't see them in list
- sys and system has pre created tables, these are data dictionary tables
- examples:
    - >SELECT * FROM all_users;
    - >SELECT * FROM tab;
    - >SELECT * FROM cat;
    - >SELECT * FROM user_tables;
    - >SELECT * FROM user_constraints;

NOTE : by looking at the structure of table we can't tell about constraints (eg: primary key, foregin key, check, etc...)

It can be seen in data dictionary table

## process of viewing constraints

command 1 :
> `desc constraints;`

used to see all constraints, from here we can choose what constraints we want to view

command 2 : 

suppose we want to view `constraint_name`, `constraint_type`, `search_condition` then following command is used
```
SELECT constraint_name,
 constraint_type,
 search_condition 
FROM user_constraints 
WHERE table_name='VOTERS';
```
this will display all constraints in details like check condition and type of key

NOTE : table name will be always in capital

for `constraint_type` 
- C = constraint
- P = primary key
- U = unique

## giving own constraint name
```
CREATE TABLE student
(
    roll_no number CONSTRAINT uni_id unique
);
```
> `roll_no` is unique

> `uni_id` is constraint name given by us

## droping constraint

```
ALTER TABLE voters drop constraint uni_id;
```
this will drop the constraint `uni_id`