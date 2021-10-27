# Keys in Table
- [Primary Key](#primary-key)
- [Foregin Key](#foregin-key)
- []()
- []()


## Primary Key
- there is only one primary key in the table
- values of that column will be `unique` and `non null`

syntax 1 :
```
CREATE TABLE student
(
    roll_no number PRIMARY KEY,
    name varchar2(20),
    marks number
);
```
> column `roll_no` will be set as primary key

syntax 2 :
```
CREATE TABLE student
(
    roll_no number,
    name varchar2(20),
    marks number,
    PRIMARY KEY(roll_no)
);
```
> column `roll_no` will be set as primary key

## Foregin Key
- it provide link b/w two tables
- it refers to the primary key of another table
- table can have more than 1 foregin key in a table
- values can be `dublicate` or `null`
- can be made both at column level as well as row/ table level

Suppose there is a table `student` with primary key `roll_no`

ROLL_NO | NAME | city
---|---|---|
1 | amit | ddn
2 | anil | mrt
3 | sunil | lkw

Now we have to create a table `sports`
```
CREATE TABLE sports
(
    roll_no number references student,
    sport varchar2(10),
);
```
> `references` is used to make a foregin key followed by table name to which we have to refer 

> while inserting data we can only enter values of `roll_no` which are present in the column of `roll_no` of  `student` table 

`sports` table
ROLL | SPORT
--- | ---
1   | Cricket
1   | Football
2   | Football

we can't insert `(8, 'football')` because 8 is not in the `student` table

> this can be possible => `(null, 'football')`
