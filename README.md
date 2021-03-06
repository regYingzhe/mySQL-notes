# mySQL-notes
### a) How to create primary keys?
1. create table employees (id int not null auto_increment primary key)
2. create table employees(id int not null auto_increment, primary key(id) )

### b) How to alter table (change the attributes when table first create)?	
e.g. alter table cats modify age int(12) not null;

### c) How to update table content? 
e.g. update cats set name="regi" where age = 10;

### d) What are the commonly used String Functions in mySQL?
1. CONCAT: select first, last, concat(first, ' ', last) as 'full name' from table; concat_ws(' - ', first, last);
2. SUBSTRING: put "" around string if there is a single quote, concat(substring(first,1,1), substring(last,1, 1));
3. REPLACE: select replace(first, 'f', 'u') from table;
4. REVERSE: select reverse(phone_number) from table;
5. CHAR LENGTH: select concat(title, 'is', char_length(title), ' words long') from table; 
6. UPPER and LOWER : select upper(name) from table;

### e) Commonly used commands to refine selection in mySQL
1. Distinct: select distinct concat(first_name, ' ', last_name) from family
2. Order by: select last_name from family order by last_name desc/asc(default). you can also do select last_name, first_name, year from family order by 2, which refer to order by year. mySQL is not 0 indexed. select first_name, last_name from family order by last_name, first_name (first sorted last_name, then sorted first_name)
3. Limit: e.g. select top 10 best selling books. select books from library order by selling_amount desc limit 10; Gotcha: limit 0,3/1,3(starting point, end point). row is 0 indexed, 0 is the first row, and 1 is the second row. specify a range used for pagination. 
4. Like: where movie_name like '%star%', wildcard % means something star something, 'star%': beginning with star then something, '%star': something end with star
5. Another wildward: '____' for specifying how many digits/characters (using escape character)
6. Union/Union all: join multiple tables with the same name of column. 

### f) Commonly used aggregates functions
1. count: select count(movie_title) from movie_2017 where movie_title like "%love%" to print out how many movies released in 2017
2. group by: select drug_name, drug_manufacture, min(released_year) from drug_store group by drug_name
3. sum: select song_writer_lname, song_writer_fname, sum(works) from songs group by song_write_lname, song_write_fname 
4. avg: select director_name, avg(selling_tickets) from movies group by director_name
5. max & min: select concat(director_fname, ' ', director_lname) as Director, Max(selling) as 'Best Movie' from movies group by director_fname, director_lname

### g) date arithmatic:
1. datediff, date_add, +/-: select birthdate, birthdate + interval 5 month from people; SELECT name, birthdate, DATEDIFF(NOW(), birthdate) FROM people; SELECT birthdt, DATE_ADD(birthdt, INTERVAL 10 SECOND) FROM people;
2. add timestamp (data type): 
create table comments (content varchar(100), create_at timestamp default now())
3. update timestamp when comment changed:
create table comments (content varchar(100), changed_at timestamp default now() on update now()/current_timestamp)
update comments set content='hello world' where content='hello regi';

### h) Joins:
1. cross join: select * from start_ups, venture_captial
2. Implicit inner join: select start_ups_name, venture_captial, invest_date, investment from start_ups, ventures where
start_up.id = venture.id
3. Explicit inner joins: select * from start_ups join ventures on start_up.id = venture.id
4. left join: 


# Tips
1. better to use alias when using joint table
2. run .sql file in the terminal by using source <fileName.sql> after login to mysql
3. using concat to build a summary of the data source
4. Storing Text: VARCHAR VS CHAR(fixed length, truncate extra chars)
5. Decimal: decimal(5,2): 888.88
6. float: 4 byte, double: 8 byte
7. Date: no time. YYYY-MM-DD; Time: no date: HH:MM:SS; DATETIME: both. curdate -> date, curtime -> time, now -> datetime,https://dev.mysql.com/doc/refman/5.7/en/date-and-time-functions.html, e.g. SELECT DATE_FORMAT(birthdt, '%m/%d/%Y at %h:%i') FROM people;
