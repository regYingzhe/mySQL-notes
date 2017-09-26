# mySQL-notes
a) How to create primary keys?
1. create table employees (id int not null auto_increment primary key)
2. create table employees(id int not null auto_increment, primary key(id) )

b) How to alter table (change the attributes when table first create)?	e.g. alter table cats modify age int(12) not null;

c) How to update table content? e.g. update cats set name="regi" where age = 10;

d) What are the commonly used String Functions in mySQL?
1. CONCAT: select first, last, concat(first, ' ', last) as 'full name' from table; concat_ws(' - ', first, last);
2. SUBSTRING: put "" around string if there is a single quote, concat(substring(first,1,1), substring(last,1, 1));
3. REPLACE: select replace(first, 'f', 'u') from table;
4. REVERSE: select reverse(phone_number) from table;
5. CHAR LENGTH: select concat(title, 'is', char_length(title), ' words long') from table; 
6. UPPER and LOWER : select upper(name) from table;

e) Commonly used commands to refine selection in mySQL
1. Distinct: select distinct concat(first_name, ' ', last_name) from family
2. Order by: select last_name from family order by last_name desc/asc(default). you can also do select last_name, first_name, year from family order by 2, which refer to order by year. mySQL is not 0 indexed. select first_name, last_name from family order by last_name, first_name (first sorted last_name, then sorted first_name)
3. Limit: e.g. select top 10 best selling books. select books from library order by selling_amount desc limit 10; Gotcha: limit 0,3/1,3(starting point, end point). row is 0 indexed, 0 is the first row, and 1 is the second row. specify a range used for pagination. 
4. Like: where movie_name like '%star%', wildcard % means something star something, 'star%': beginning with star then something, '%star': something end with star
5. Another wildward: '____' for specifying how many digits/characters (using escape character)
f) Commonly used aggregates functions
1. count: select count(movie_title) from movie_2017 where movie_title like "%love%";
2. group by: select drug_name, drug_manufacture, min(released_year) from drug_store group by drug_name
3. sum: 
# Tips
1. better to use alias when using joint table
2. run .sql file in the terminal by using source <fileName.sql> after login to mysql
3. using concat to build a summary of the data source
