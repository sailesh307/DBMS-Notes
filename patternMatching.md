# Pattern Matching
table `student`
ROLLNO | NAME | CITY
--- | --- | ---
1   | Amit | Kanpur 
2   | Anil | kaNpur
3   | Ankit| KANpur
4   | Anuj | KANPUR
5   | Sam  | Doon

```
SELECT * FROM student WHERE UPPER(city) = 'KANPUR';
```
this will print all rows where `city` = 'KANPUR'

```
SELECT * FROM student WHERE name LIKE 'A%';
```
this will print all details where `name` starts from A

- A% => 0 or more char after `A`
- %A => 0 or more char before `A`
- %A% => 0 or more char before or after `A`
- A_ => exactly one char after `A`
- A__ => exactly two char after `A`

```
SELECT * FROM student WHERE name NOT LIKE 'A%';
```
this will print all details where name does not start wit `A`

#  Handling NULL Values

table `student`
ROLLNO | NAME | FEE
--- | --- | ---
1   | Amit | 100 
2   | Anil | 
3   | Ankit| 100
4   | Anuj | 
5   | Sam  | 100

to print details where `FEE` is null
```
SELECT * FROM student WHERE fee IS NULL;
```
OUTPUT : 

ROLLNO | NAME | FEE
--- | --- | ---
2   | Anil | 
4   | Anuj | 

**Note :** 
- don't use `city = null`, because it is only null not any other values `('', "", 0)`
- if we use `city = null` then nothing will print


## Filling `null` values while displaying
```
SELECT NVL(fee, 0) FROM student;
```
>this will print `0` if `FEE` is null, insted of `0` we can write any other value

OUTPUT :

NVL(FEE, 0)|
---|
100
0
100
0
100

## Use of NVL function
- used to fill `null` values
- used in calculations

eg : 

```
SELECT AVG(fee) FROM student;
```
**OUTPUT:**

AVG(NVL(FEE, 0))|
---|
100

> avg is calculated as `avg = sum of values / no. of non-null values`
>
> avg = (100 + 100 + 100)/3 = 100

for handing this `NVL function` is used
```
SELECT AVG(NVL(fee), 0) FROM student;
```
**OUTPUT:**

AVG(NVL(FEE, 0))|
---|
60

> avg = (100 + 0 + 100 + 0 + 100)/5 = 60
