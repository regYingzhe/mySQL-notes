# mySQL-notes
How to create primary keys?
1. create table employees (id int not null auto_increment primary key)
2. create table employees(id int not null auto_increment, primary key(id) )
How to alter table (change the attributes when table first create)?
alter table cats modify age int(12) not null;
# Tips
1. better to use alias when using joint table
