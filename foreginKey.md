# Foregin Key
- Condition to use foregin Key : parent table should have primary Key
- It is a attribute whose values are dependent on another column(i.e Primary Key)
- It is a child column which is dependent on another Parent column (i.e Primary Key) for its values
- A table can have more than 1 Foregin Key
- It can contain `null` and `duplicate` values
- It can be made both at column and row/table level.

# Creation of Foregin Key

Suppose there is a table `student` with primary key `roll_no`

ROLL_NO | NAME | city
---|---|---|
1 | amit | ddn
2 | anil | mrt
3 | sunil | lkw

Now we have to create a table `sports`

## Column Level
```
CREATE TABLE sports
(
    roll_no number references student,
    sport varchar2(10),
);
```
> `references` is used to make a foregin key followed by table name to which we have to refer 

> while inserting data we can only enter values of `roll_no` which are present in the column `roll_no` of  `student` table 

`sports` table
ROLL | SPORT
--- | ---
1   | Cricket
1   | Football
2   | Football

we can't insert `(8, 'football')` because 8 is not in the `student` table

> this can be possible => `(null, 'football')`


## Row/Table Level

```
CREATE TABLE table_name
(
    col_name1 datatype,
    col_name2 datatype,
    FOREGIN KEY(col_name1) REFERENCES old_table
);
```
eg : 
```
CREATE TABLE sports
(
    roll_no number,
    sport varchar2(10),
    FOREGIN KEY(roll_no) REFERENCES student
);
```


---
### **A Table can be parent of its own table**
eg : 
```
CREATE TABLE manager
(
    empcode number PRIMARY KEY,
    eName varchar2(20),
    city varchar2(20),
    mgr number REFERENCES manager
);
```
EMPCODE | ENAME | CITY | MGR
--- | --- | --- | ---
101 | Amar | DDN | 
201 | Bharat | MRT | 101
301 | Kapil | MRT | 101

> here `EMPCODE` is primary key

> `MGR` is Foregin Key

# Foregin Key as Primary Key
simply add a primary key to that column 
```
ALTER TABLE tableName ADD PRIMARY KEY(col_name);
```
if we want to make it at the time of creation of table

eg:
```
CREATE TABLE sports
(
    rollNo number PRIMARY KEY REFERENCES student,
    name varchar2() 
);
```

---
# Two Tpes of Foregin Key
- **Atomic Foregin Key** : Single column
    - eg: roll_no, student_id, ...
- **Composite Foregin Key** : Multiple columns

eg. of composite foregin key: 

table `orders`
ORDERNO | ITEMNO | NAME
--- | --- | ---
1   | 10  | Coke
2   | 20  | Pepsi
3   | 20  | Samosa  
> in this table `orderNO` and `IteamNo` together are `primary key`

Now we have to make a table `orderStatus`
```
CREATE TABLE orderStatus
(
    ordreNo number,
    itemNo number,
    status varchar2(10),
    PRIMARY KEY(orderNo, itemNo),
    FOREGIN KEY(orderNo, itemNo) REFERENCES orders
);
```
> in this table `orderNo`, `itemNo` are made as primary key and foregin key

> this table will refer to the table `orders`