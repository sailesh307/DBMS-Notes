# CHECK
- used to apply restriction on any column
- `CHECK` keyword is used
```
CREATE TABLE voters
(
    id number,
    name varchar2(20),
    age number CHECK (age>=18 AND age<100),
    sex varchar2(10) CHECK(sex IN ('male', 'female'))
);
```
> in this table we can only add `age >=18` and `sex should be either male or female`


# DEFAULT
- used to give deafult values to a column
```
CREATE TABLE voters
(
    id number,
    name varchar2(20),
    age number DEFAULT 18
);
```
> if only name is inserted into the table then `age` will be set to 18 by default

>`INSERT INTO voter(id, name) values(10, 'amit');`

>`INSERT INTO voter(id, name, age) values(10, 'amit', default);`

both are same thing