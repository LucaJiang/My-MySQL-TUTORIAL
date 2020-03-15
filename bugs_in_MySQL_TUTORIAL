# Bugs_in_MySQL_Tutorial
record bugs in https://www.mysqltutorial.org/  's tutorial

## contents

* [**JOIN**](#join)
* [**SEQUENCE**](#SEQUENCE)

## JOIN

location: https://www.mysqltutorial.org/mysql-join/

There exists the same bug within section join. So, i use inner join as an example.

### origin:
```MySQL
SELECT 
    m.member_id, 
    m.name member, 
    c.committee_id, 
    c.name committee
FROM
    members m
INNER JOIN committees c 
    ON c.name = m.name;
```
### log:    
~~~
ERROR 1064 (42000): You have an error in your SQL syntax;
check the manual that corresponds to your MySQL server version for the right syntax to use near ',
    c.committee_id,
    c.name committee
FROM
    members m
INNER JOIN commi' at line 3
~~~
### correct code:
```MySQL
SELECT 
    m.member_id, 
    m.name, 
    c.committee_id, 
    c.name
FROM
    members m
INNER JOIN committees c 
    ON c.name = m.name;
```

## SEQUENCE

location: https://www.mysqltutorial.org/mysql-sequence/

In **"How MySQL sequence works"**:

*If you use the UPDATE statement to update values in the AUTO_INCREMENT column to a value that already exists, MySQL will issue a duplicate-key error if the column has a unique index. If you update an AUTO_INCREMENT column to a value that is greater than the existing values in the column, MySQL will use the next number of the last insert sequence number for the next row. For example, if the last insert sequence number is 3, you update it to 10, the sequence number for the new row is 4.*

I had tried with MySQL 8.0, and  found that UPDATE would affect the index of AUTO_INCREMENT. So, it should be:

*If you use the UPDATE statement to update values in the AUTO_INCREMENT column to a value that already exists, MySQL will issue a duplicate-key error if the column has a unique index. If you update an AUTO_INCREMENT column to a value that is greater than the existing values in the column, MySQL will use the next number of the **updated sequence** number for the next row. For example, if the last insert sequence number is 3, you update it to 10, the sequence number for the new row is **11**.*
