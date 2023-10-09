In MySQL Workbench. Some basic commands:

`show databases` - show databases in my database

`create database <name_of_database>` - create new database

- one line comment in mysql database `#
- multi line comment in mysql database `/*  ... */`
- close line `;`
- types: integer, varchar(size), date

To connect python with MySQL mysql-connector-python is requaired:

```shell
pip install mysql-connector-python
```

### SQL BASICS:

1) Create new database:

```shell
create database <database_name>
```

2) Remove existing database:

```shell
drop database <database_name>
```

3) To use interested database after creating it type:

```shell
use <database_name>
```

4) Create table in databases type name and names and type of columns between brackets.

```shell
create table <table_name>(id integer, first_name varchar(10), last_name varchar(10)) 
```

5) To insert some value into the table

```shell
insert into customer_info(<columnsname>) values(<values_for_columns>)
```

6) To remove table

```shell
drop table <table_name>
```

7) To display content of tha table

```shell
select * from <table_name>
```

Example:

```shell;
create datanase customers;
use customers;
show tables;
create table customer_info(id integer, first_name varchar(10), last_name varchar(10));
show tables;
select * from customer_info;
insert into customer_info(id,first_name,last_name) values(1,'Name','Surname');
select * from customer_info;
drop table customer_info;
show tables;
drop database customers;
show databases;
```

8) Auto incrementation. Add `auto_increment` while after column integer definition
9) While defining table at the end add `primary key(<column_name>)` to make them unique
10) To check if there is null/not null value in selected column
```shell
select * from <table_name> where <column_name> is null
select * from <table_name> where <column_name> is not null
```
11) How to update statement to replace null values
```shell
update <table_name> set <column_name>=<new_value> where <condition>=<value>
```
12) Delete statement removes entire row
```shell
delete from customer_info where <column_name>=<value>;
```
13) Add/modify/drop column in the existing table
- alter table <table_name> add <column_name> <type>;
- alter table <table_name> modify <column_name> <new_data_type>
- alter table <table_name> drop column <column_name>

14) To check the schema of the table
```shell
desc table
```

### MySQL Constraints 
SQL constraints are used to specify any rules for the records in a table.
Constraints can be used to limit the type of data that can go into a table.
It ensures the accuracy and reliability of the records in the table, and if there is 
any violation between the constraint and the record action, the action is aborted. 
Constraints can be column level or table level. Column level constraints aplly to a column, 
and table-level constraints apply to the whole table. 
1) Not Null
2) Unique
3) Primary Key
4) Foreign Key
5) Check
6) Default
7) Index


### MySQL Indexes
CREATE INDEX state,emt in SQL is used to create indexes in tables.
The indexes are used to retrieve data from the database more quickly than others.
The user can not see the indexes, and they are just used to speed up queries/searches.
Note: Updating the table with indexes takes a lot of time than updating a table without indexes.
It is because the indexes also need update. 
So, only create indexes on those columns that will be frequently searched against. 
This is mean:
- for querying, it is efficient, but
- for insert/update/alter it will slow down the processing


### Views in MySQL
View is a virtual table based on the results set of an SQL query.

CREATE VIEW <name> as <querry>

! Remember views are not possible to create for any kind of modifying quarries such as 
alter/update/aggregate etc. 


### SQL Joins
1) Inner Join - pick the values which match in selected tables
2) Left Join - show all from left table and nulls if there are more which no match in right table
3) Right Join - show all from right table and nulls if there are more which no match in the left table
4) Full Join - union of left and right join
5) Natural Join - all possible combination
6) Cross Join

### My SQL Store procedure
It is something like a function. After defining a procedure it can be called using 

`call <procedure_name>`

It is also possible to call a procedure with parameters. To do this during creating procedure in the bracket:
- IN/OUT/INOUT
- column name
- type
- For example: `PROCEDURE get_something(IN par_name INT)`

For `OUT` it will provide some information into the record. 
It needs to be assigned into some parameter by @record as procedure input. 

For example
`call <procedure_name>(@record);`


### Misc
1) `LIKE` - define specific keyword, regular expression could be after this in ''.
2) `BETWEEN` - to determine some range between two values.
3) `CONCAT()` - works like os.path.join()
4) `AS` -assigned query into more friendly name
5) `GROUP BY` - useful for calculating in different categories. 
6) `= is` and  `IN()` are the same 
7) `ON DELETE CASCADE` - while creating `foreign key` with other table it will link them if some record will be deleted
8) 





