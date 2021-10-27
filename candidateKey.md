# Candidate Key

ECODE | ENAME | DCODE | PPNO | CITY | VOTERID
---|---|---|---|---|---
101 | anurag | 40 | 8899 | delhi | 10001
201 | kapil | 10 | 2233 | haridwar | 90009
301 | mudit | 40 | 5566 | delhi | 70007

- a column which has the features of becoming a Primary Key
    - eg: `ecode`, `voterid`, `ppno` (passport no)

# Alternate Key
- columns left out of candidate keys after selecting primary key
    - eg: if `ecode` is selected as primary key
    - then `voterid`, `ppno` will be alternate key

# Secondary Key
- it is not a true key
- but can be used to extract selected records
- eg : `SELECT * FROM employee WHERE city = 'delhi';`
- city is acting as secondary key

# Super Key
- any valid combination of Primary key with other attribute is super key
    - `ecode` is super key
    - `ecode`, `ename` is also super key
    - `ecode`, `ename`, `dcode` is also super key
- primary key is the smallest super key
- super key = primary key + other attributes