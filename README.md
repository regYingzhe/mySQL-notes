# mySQL-notes
How to create primary keys?
1. create table employees (id int not null auto_increment primary key)
2. create table employees(id int not null auto_increment, primary key(id) )

How to alter table (change the attributes when table first create)?	e.g. alter table cats modify age int(12) not null;

How to update table content? e.g. update cats set name="regi" where age = 10;

What are the commonly used String Functions in mySQL?
1. CONCAT
2. SUBSTRING
3. REPLACE
4. REVERSE
5. CHAR LENGTH
6. UPPER and LOWER
# Tips
1. better to use alias when using joint table
2. run .sql file in the terminal by using source <fileName.sql> after login to mysql
