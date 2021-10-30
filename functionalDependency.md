# Functional Dependency (FD)
- It is a relationship that exists between two attributes.
- It typically exists between the primary key and non-key attribute within a table
- it is a unique relation from `X` to `Y` i.e for each value of X there exist only one value of Y

**Representation** 
> `X -> Y`

**Read as :**<br> `X` determines `Y` <br> OR <br> `X` identifies `Y` <br> OR <br> `Y` is dependent on `X` for its value

where
- `X` is a determinant 
- and `Y` is a dependent.

## Valid FDs
- which can uniquely identify a value of `Y` from a value of `X`
- eg :
    - `RollNo -> Name`  [for each roll no there is only one name]
    - `RollNo -> City` [for each roll no there is only one city]

## Invalid FDs
- more than one value of `X`
- eg : 
    - `Name -> RollNo` [names are not unique so there can be more than one student with same name]
    - `City -> RollNo` [cities are not unique so there can be more than one student from same city]

## Set of FDs `F` on Relation `R`
- `R` is a relation
- `F` is a set of FDs on `R`

EXAMPLES:
- eg1 : `R` : STUDENT(`RollNo`, `Name`, `City`)<br> $~~~~~~~$ `F` : {`RollNo -> Name`, `RollNo -> City`}

- eg 2 : `R(ABC)` <br> $~~~~~~~~$ F = {`A -> B`, `A -> C`}

Sincce above table has total 3 attribues and `A` determines both `B` and `C`, `A` is candidate key [which which is capable of becoming primary key] of table

## Partial Dependency
- this occur when a primary key made up of more than one column(`AB`)[`A` -> column 1, `B` -> column 2]] 
- when a non-prime attribute(`Y`) is functionally dependent on part of a candidate key.

**EXAMPLE :** <br>
let `{A, B}` is the primary key and `C` is not a key attribute then if `{A, B} -> C` and `A-> C` or `B->C` then `C` is partially dependent on `{A, B}`

## Full Dependency
- when `Y` can't be identified individually from any part of `X` [either A or B] but it can only be identified from both A and B.

**EXAMPLE :** <br>
let `{A, B}` is the primary key and `C` is not a key attribute then if `{A, B} -> C` and `A-> C` and `B->C` then `C` is fully dependent on `{A, B}`

## Transitive Dependency
- it is similar to transitive in mathematics
- if `A -> B` and `B -> C` then `A -> C`

