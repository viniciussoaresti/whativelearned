# Databases:

"A database is an organized collection of structured information, or data,
typically stored electronically in a computer system. A database is usually
controlled by a database management system (DBMS)", 
[Oracle](https://www.oracle.com/database/what-is-database/#:~:text=A%20database%20is%20an%20organized,database%20management%20system%20(DBMS).).

# Contents:

- [Databases:](#databases)
- [Contents:](#contents)
- [SQL:](#sql)
  - [Common commands:](#common-commands)
    - [SELECT:](#select)
    - [UPDATE:](#update)
    - [DELETE:](#delete)
    - [INSERT INTO:](#insert-into)
    - [CREATE DATABASE:](#create-database)
    - [ALTER DATABASE:](#alter-database)
    - [CREATE TABLE:](#create-table)
    - [ALTER TABLE:](#alter-table)
    - [DROP TABLE:](#drop-table)
    - [CREATE INDEX:](#create-index)
    - [DROP INDEX:](#drop-index)
  - [Common clauses:](#common-clauses)
    - [WHERE:](#where)
    - [GROUP BY:](#group-by)
    - [HAVING:](#having)
    - [ORDER BY:](#order-by)
    - [GROUP BY:](#group-by-1)
  - [Common operators:](#common-operators)
    - [Arithmetic:](#arithmetic)
    - [Bitwise:](#bitwise)
    - [Comparison:](#comparison)
    - [Compound:](#compound)
    - [Logical:](#logical)
  - [Joins:](#joins)
- [DBMS:](#dbms)
- [Good practices:](#good-practices)
  - [Table primary key (PK):](#table-primary-key-pk)
    - [1 - Primary keys should be as small as necessary:](#1---primary-keys-should-be-as-small-as-necessary)
    - [2 - Primary keys should never change:](#2---primary-keys-should-never-change)
    - [3 - Do NOT use "your problem primary key" as your logic model primary key:](#3---do-not-use-your-problem-primary-key-as-your-logic-model-primary-key)

# SQL:

"SQL is a programming language used by nearly all relational databases to query,
manipulate, and define data, and to provide access control",
[Oracle](https://www.oracle.com/database/what-is-database/#:~:text=A%20database%20is%20an%20organized,database%20management%20system%20(DBMS).).

## Common commands:

### SELECT:

```sql
SELECT * FROM student;
```

### UPDATE:

### DELETE:

### INSERT INTO:

### CREATE DATABASE:

### ALTER DATABASE:

### CREATE TABLE:

### ALTER TABLE:

### DROP TABLE:

### CREATE INDEX:

### DROP INDEX:

## Common clauses:

### WHERE:

```sql
SELECT * FROM student WHERE id = 1;
```

```sql
SELECT * FROM student WHERE name like "j%";
```

### GROUP BY:

### HAVING:

### ORDER BY:

### GROUP BY:

## Common operators:

### Arithmetic:

`+`, `-`, `*`, `/`, `%`;

### Bitwise:

`&`, `|`, `^`;

### Comparison:

`=`, `>`, `<`, `>=`, `<=`, `<>`;

### Compound:

`+=`, `-=`, `*=`, `/=`, `%=`, `%=`, `&=`, `^-=`, `|*=`;

### Logical:

`ALL`, `AND`, `ANY`, `BETWEEN`, `EXISTS`, `IN`, `LIKE`, `NOT`, `OR`, `SOME`;

## Joins:

"In SQL, an inner join is not considered a specific clause, operator, or command
on its own. Instead, it is a type of join operation that combines rows from
multiple tables based on a specified condition", 
[ChatGPT](https://chat.openai.com/share/c2c7eef3-9b6d-4952-b676-9f33b0557d61).

# DBMS:

"A database typically requires a comprehensive database software program known as
a database management system (DBMS). A DBMS serves as an interface between the
database and its end users or programs, allowing users to retrieve, update, and
manage how the information is organized and optimized. A DBMS also facilitates
oversight and control of databases, enabling a variety of administrative
operations such as performance monitoring, tuning, and backup and recovery",
[Oracle](https://www.oracle.com/database/what-is-database/#:~:text=A%20database%20is%20an%20organized,database%20management%20system%20(DBMS).).

# Good practices:

## Table primary key (PK):

### 1 - Primary keys should be as small as necessary:

Prefer a numeric type because numeric types are stored in a much more compact
format than character formats. This is because most primary keys will be foreign
keys in another table as well as used in multiple indexes. The smaller your key,
the smaller the index, the less pages in the cache you will use.

### 2 - Primary keys should never change:

Updating a primary key should always be out of the question. This is because it
is most likely to be used in multiple indexes and used as a foreign key.
Updating a single primary key could cause of ripple effect of changes.

### 3 - Do NOT use "your problem primary key" as your logic model primary key:

For example passport number, social security number, or employee contract number
as these "natural keys" can change in real world situations. Make sure to add
UNIQUE constraints for these where necessary to enforce consistency.

Topics 1, 2 and 3 from [here](https://stackoverflow.com/questions/337503/whats-the-best-practice-for-primary-keys-in-tables).