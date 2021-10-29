# Codd Rules



## Rule 0 The Foundation Rule
- The databse must be in relational form.
- So that the system can handle the database through its relational capabilities.
## Rule 1 Information Rule
- All data should be presented to the user in table form.

## Rule 2 Guaranteed Access Rule
- Data should be accessible without any ambiguity.
- Uses table name, primary key, column name to uniquely access single piece of data -> atomic data.

## Rule 3 Systematic Treatment of Null Values
- A field should be allowed to remain empty.
- null value is not equal to empty string or number 0
- The null value has various meanings in the database, like 
    - missing the data, 
    - no value in a cell, 
    - inappropriate information, 
    - unknown data and 
    - the primary key should not be null.

## Rule 4
- Dynamic on-line catalog based on the relational model(Data Dictionary)(internal tables are called data dictionary) table
- Provide access to its structure through the same tools that are used to access the data.

## Rule 5 Comprehensive Data Sublanguage Rule
- the database must support at least one clearly defined language.

## Rule 6 View Updating Rule
- All views table can be theoretically updated and must be practically updated by the database systems.


[MORE ABOUT VIEWS](#views)

## Rule 7
- The system must support INSERT, UPDATE, and DELETE operations.

## Rule 8 Physical Data Independence Rule
- The data must be independent of the physical structure of the database.

## Rule 9 Logical Data Independence Rule
- The data must be independent of the logical structure of the database.
- eg: adding a new column to a table should not affect the data in the table.

## Rule 10 Integrity Rule
- The database language should support constraints on user input that maintain the integrity of the database.
- eg: Primary key

## Rule 11 Distribution Independence Rule
- A user should be totally unaware of the distribution of the data in the database.

## Rule 12 Non Sunversion Rule
-  If a system has a low-level or separate language other than SQL to access the database system, it should not  bypass integrity to transform data.

- simply no other language can modify the rules of database.







<br>
<br>
<br>
<br>
<br>

# Views

**There are two types of views:**
- **Simple**  : that does not contain any formula or function
    - eg:
    - > CREATE VIEW view_name AS SELECT col1, col2 FROM table_name;

    - How to use:
    - > SELECT * FROM view_name;

    - this can be used in place of `SELECT col1, col2 FROM table_name;`
- **Complex** : that contain formula or function
    - eg: 
    - > CREATE VIEW view_name As SELECT name, marks + 10 newMarks FROM student;

NOTE : details of views are stored in data dictionary table.

# Changing name while displaying

suppose we have a table called `student`
ROLL_NO | NAME | MARKS
--------|------|-------
1       | a    | 100
2       | b    | 200
3       | c    | 300
4       | d    | 400

if below query is executed
```
SELECT name, marks + 10 FROM student;
```
output will be:

 NAME | MARKS+10
------|-------
 a    | 110
 b    | 210
 c    | 310
 d    | 410

so to display the Marks+10 witha proper name we can use the following query
```
SELECT name, marks + 10 AS new_marks FROM student;
```
OR
```
SELECT name, marks + 10 new_marks FROM student
```
OR
```
SELECT name, marks + 10 AS "new marks" FROM student;
```
> Note : if we want spaces in column heading we can use double quotes
OUTPUT :

 NAME | NEW MARKS
------|-------
 a    | 110
 b    | 210
 c    | 310
 d    | 410

 ## inserting values into view 
 - we can only insert values in simple views not in complex views
 ```
INSERT INTO view_name VALUES (1, 'a', 100);
 ```
