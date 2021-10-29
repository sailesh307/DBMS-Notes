# Date Format
- DD-MON-YY,$~~~$ eg: 25-JAN-19
- DD-MON-YYYY,$~~~$ eg: 25-JAN-2019
- DD-MON-RR

> Make a table to store name and dob of students

**Table Creation:**
```
CREATE TABLE student
(
    id NUMBER,
    dob DATE
);
```
**Data Insertion**
```
INSERT INTO student VALUES(1,'25-JAN-19');
INSERT INTO student VALUES(2,'21-JUN-19');
INSERT INTO student VALUES(3,'03-JUN-19');
```

**OUTPUT Table**
ID | DOB
---|---
1  | 25-JAN-19
2  | 21-JUN-19
3  | 03-JUL-19

> NOTE: by default, the date format is DD-MON-YY

> `12-08-19` this is invalid date format

> `12/MAR/19` this is valid and will be stored as `12-MAR-19`

> `12-MAR-2019` this is valid and will be stored as `12-MAR-19`

> `sysdate` is used to display current date

NOTE : any symbol can be used in place of `-`

## how to view complete format of date
**1st Way:**

eg: view `05-JAN-2019` which is stored as `05-JAN-19` in table

```
SELECT ID, TO_CHAR(DOB,'DD-MON-YYYY') FROM student;
```

**2nd Way :**
- to change the dispaly format of current session
```
ALTER SESSION SET NLS_DATE_FORMAT = 'DD-MON-YYYY';
```
> NLS = National Language Support

> this will change the format of date from DD-MON-YY to DD-MON-YYYY for currect session (in table + query)

> this method is best

Now table will look like this
ID | DOB
---|---
1  | 25-JAN-2019
2  | 21-JUN-2019
3  | 03-JUL-2019

## Formats of date
- DAY = sunday, monday, tuesday, 
- MONTH = january, february, march
- MON = jan, feb, mar
- YEAR = nineteen seventy nine
- YYYY = 2019, 2020, 2021
- YY = 19, 20, 21
- DD = 01, 29, 31
- %ss = used => DDss =>eg if DD is 10 then DDss will be TEN
ss is used to spell out the number
eg of ss : 
- DDss : 10 => TEN
- YYss : 21 => twenty one

combine these format to get your desired format

eg:
> `DAY-DD-MON-YYYY` => `sunday-10-jan-2019`

## Format of Time
eg : `DD-MON-YYYY-HH:MI:SS` => `25-JAN-2019-12:00:00`

default 12:00:00 am is used for time if time is not given for a date

if `sysdate` is used in query then it will display current time

## inserting time in table
**using to_date() function**
```
INSERT INTO student VALUES(20, to_date('25-JAN-2019 11:11:11','DD-MON-YY HH:MI:SS'));
```

by deafult we cant see tie in table so we have to change the format of date using `ALTER SESSION`
```
ALTER SESSION SET NLS_DATE_FORMAT = 'DD-MON-YY HH:MI:SS';
```

# Operatons on date

## current sysdate = `28-oct-2021`
```
SELECT sysdate + 2 FROM DUAL;
```
OUTPUT : `30-oct-2021`

```
SELECT sysdate - 10 FROM DUAL;
```
OUTPUT : `18-oct-2021`

```
SELECT sysdate - to_date(20-oct-2019) FROM DUAL;
```
OUTPUT : `739.348715`
> output will be in no. of days and the values after point represents time in days

> to remove values after point(.) use trunc() function or round() function

> to dispay no. of years from output simply divide it by 365



# common commands
`sysdate = 28-oct-2021`

<!-- cmd1 -->

> Display current date 

```
SELECT current_date FROM DUAL;
```
OUTPUT : `28-OCT-2021`


<!-- cmd2 -->
>  add 2 month to sysdate

```
SELECT add_months(sysdate,2) FROM DUAL;
```
**OUTPUT :** `28-DEC-2021`

<!-- cmd3 -->
>  display current time stamp
```
SELECT CURRENT_TIMESTAMP FROM DUAL;
```
**OUTPUT :** 28-OCT-21 08.34.17.735000 AM +05:30

<!-- CMD4 -->
> display last day of current month
```
SELECT LAST_DAY(sysdate) FROM DUAL;
```

<!-- cmd5 -->
> display next day of current month (find next sunday of this month)
```
SELECT NEXT_DAY(sysdate,'SUN') FROM DUAL;
```