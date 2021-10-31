# Relational Algebra
- It is a formal language of interaction with RDBMS. Its primary operations are:
1. Selection (σ)
2. Projection (π)
3. Union (∪)
4. Intersection (∩)
5. Minus or Difference (-)
6. Cartesian Product (×)
7. Join (⋈)
8. Rename (ρ)

Example : Consider `STUDENT` relation(Table)

RollNo | Name | City
------ | ---- | ----
1     | A    | DDN
2     | B    | MRT
3     | C    | MRT
4     | A    | HRD

## Projection (π)
- This operation is used to select vertical columns from the relation(table)(vertical slicing).

<img src="https://latex.codecogs.com/png.image?\dpi{110}&space;\bg_white&space;\inline&space;\pi_{rollNo}(STUDENT)" title="π(STUDENT, rollNo)" />

this will give

ROLLNO |
------ |
1     |
2     |
3     |
4     |

SQL : `SELECT rollNo FROM STUDENT;`

## Selection (σ)
- This operation is used to display horizontal rows from of the relation(table)(horizontal slicing).

<img src="https://latex.codecogs.com/png.image?\dpi{110}&space;\bg_white&space;\inline&space;\sigma_{city=HRD}(STUDENT)" title="σ_{city=HRD}(STUDENT) =" />

rollNo | Name | City
------ | ---- | ----
4     | A    | HRD

**Question :** Display names of Students who are from MRT.

**Solution:** First `σ(select)` then `π(project)`

- 1st all details of student who are from `mrt` will be extracted from table `σ(select)` 
- then out of this only `name` will be extracted `π(project)`

<img src="https://latex.codecogs.com/png.image?\dpi{110}&space;\bg_white&space;\inline&space;\pi_{name}(\sigma_{city=MRT}(STUDENT)" title="\bg_white \inline \pi_{name}(\sigma_{city=MRT}(STUDENT)" />

Output will be =>

name |
---- |
B    |
C    |

## Union (∪)
- Used to display elements all elements without duplicates.

Suppose

`P = {A, B, C}`

`Q ={A, D}`

then, `P ∪ Q = {A, B, C, D}`

SQL : `SELECT * FROM table1 UNION SELECT * FROM table2;`

## Intersection (∩)
- Used to display elements common to both sets.

taking same example, `P ∩ Q = {A}`

SQL : `SELECT * FROM table1 INTERSECT SELECT * FROM table2;`

## Minus or Difference (-)
- Used to display elements of first set after removing second set elements.

taking same example, `P - Q = {B, C}`

SQL : `SELECT * FROM table1 MINUS SELECT * FROM table2;`

