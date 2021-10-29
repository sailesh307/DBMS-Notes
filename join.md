# Cartesian product

table `one`

NAME | CITY
---- | ----
abc  | ddn
def  | mrt
mno  | ddn
ghi  | hrd


Table `two`

NAME | HOBBY
---- | -----
abc  | cricket
abc  | songs
ghi  | painting
mno  | painting
def  | tracking
mno  | skating

How to find Cartesian product of two tables?
```
SELECT * FROM one CROSS JOIN two;
```
OR
```
SELECT * FROM one, two;
```
This will give cartesian product of two tables.[as in maths each row of first table is multiplied with each row of second table]

OUTPUT : 

NAME |CITY | NAME | HOBBY
-----|-----|------|------
abc  | ddn | abc  | cricket
abc  | ddn | abc  | songs
abc  | ddn | ghi  | painting
abc  | ddn | mno  | painting
abc  |ddn  | def  | tracking
abc  |ddn  | mno  | skating
def  |mrt  | abc  | cricket
def  |mrt  | abc  | songs
def  |mrt  | ghi  | painting
def  |mrt  | mno  | painting
def  |mrt  | def  | tracking
def  |mrt  | mno  | skating
mno  |ddn  | abc  | cricket
mno  |ddn  | abc  | songs
mno  |ddn  | ghi  | painting
mno  |ddn  | mno  | painting
mno  |ddn  | def  | tracking
mno  |ddn  | mno  | skating
ghi  |hrd  | abc  | cricket
ghi  |hrd  | abc  | songs
ghi  |hrd  | ghi  | painting
ghi  |hrd  | mno  | painting
ghi  |hrd  | def  | tracking
ghi  |hrd  | mno  | skating


# JOIN
- A join is a cartesian product followed by a condition.
- Types of joins
    - [equi join](#equi-join) :- joining on some equal condition
    - [natural join](#natural-join) :- joning when column name is same
    - [inner join or non-equi join](#inner-join-or-non-equi-join)
    - [Outer Join](#outer-join)
        - left outer join
        - right outer join
        - full outer join
    - Self Join

Tables are : 

table `one`

NAME | CITY
---- | ----
abc  | ddn
def  | mrt
mno  | ddn
ghi  | hrd

Table `two`

NAME | HOBBY
---- | -----
abc  | cricket
abc  | songs
ghi  | painting
mno  | painting
def  | tracking
mno  | skating

## Equi join
- Joining on some equal condition is called `equi join`.
```
SELECT * FROM one, two WHERE one.NAME = two.NAME;
```
OUTPUT :

NAME | CITY| NAME | HOBBY
-----|-----|------|-------
abc  | ddn | abc  | cricket
abc  | ddn | abc  | songs
ghi  | hrd | ghi  | painting
mno  | ddn | mno  | painting
def  | mrt | def  | tracking
mno  | ddn | mno  | skating

## Natural join
- Natural join is a join when column name is same.
```
SELECT * FROM one NATURAL JOIN two;
```
OUTPUT :

NAME | CITY| HOBBY
-----|-----|-------
abc  | ddn | cricket
abc  | ddn | songs
ghi  | hrd | painting
mno  | ddn | painting
def  | mrt | tracking
mno  | ddn | skating

> Note : it will remove the extra column and can only be used when column name in both table are equal.

NOTE : in all above codes first cartesian will be performed then condition is applied[eg: where one.NAME = two.NAME, natural join]


## Inner join or non-equi join
- only performing join on selected columns
```
SELECT one.NAME, two.HOBBY FROM one, two WHERE one.NAME = two.NAME;
```
OUTPUT :

NAME | HOBBY
-----| ------
abc  | cricket
abc  | songs
ghi  | painting
mno  | painting
def  | tracking
mno  | skating

**Ques 1 :** Perform join on selected columns[all columns of table `one` and `hobby` column of table `two` with same name]
```
SELECT one.*, two.HOBBY FROM one, two WHERE one.NAME = two.NAME;
```
OUTPUT :

NAME | CITY | HOBBY
---- | -----| ------
abc  | ddn  | cricket
abc  | ddn  | songs
ghi  | hrd  | painting
mno  | ddn  | painting
def  | mrt  | tracking
mno  | ddn  | skating

## Outer Join
- returns all rows from both tables which satisfy or don't satisfy the join condition
- `+` is used only on one side of the join condition.
