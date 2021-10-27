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
