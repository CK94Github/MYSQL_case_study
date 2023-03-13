# MYSQL_case_study

mySQL_case_study__for_practice_whichcover_many_queries

create table grocery(s_id primary key,p_name varchar(20), price float;

insert into grocery(s_id,p_name,price)values(1,"oil",130),(2,"suger",50),(3,"wheat",40);

MariaDB [chaitanya]> select * from grocery;

+------+--------+-------+
| s_id | p_name | price |
+------+--------+-------+
|    1 | oil    |   130 |
|    2 | suger  |    50 |
|    3 | wheat  |    40 |
+------+--------+-------+
MariaDB [chaitanya]> select * from electronics;
+------+---------+-------+------+
| p_id | product | stock | s_id |
+------+---------+-------+------+
|  101 | TV      |    13 |    1 |
|  102 | AC      |    22 |    2 |
|  107 | iron    |    16 |    3 |
+------+---------+-------+------+
MariaDB [chaitanya]> select * from garments;
+------+-------------+----------+------+
| g_id | brand       | materail | p_id |
+------+-------------+----------+------+
|  201 | raymond     | jute     |  101 |
|  202 | cotton_king | cotton   |  102 |
|  203 | siyaram     | leather  |  107 |
+------+-------------+----------+------+

MariaDB [chaitanya]> select * from mobiles;
+---------+-------+------+
| brand   | stock | RAM  |
+---------+-------+------+
| samsung |    20 |    4 |
| apple   |    12 |    8 |
| nokia   |    10 |    2 |
+---------+-------+------+

create table grocery(s_id primary key,p_name varchar(20), price float;

insert into grocery(s_id,p_name,price)values(1,"oil",130),(2,"suger",50),(3,"wheat",40);

create table electronics(p_id int primary key, product varchar(20), stock int,s_id int,foreign key(s_id) references grocery(s_id));

insert into electronics(p_id,product,stock,s_id)values(101,"TV",13,1),(102,"AC",22,2),(107,"iron",16,3);

insert into garments(g_id,brand,materail,p_id)values(201,"raymond","jute",101),(202,"cotton_king","cotton",102),(203,"siyaram","leather",107);

insert into mobiles(brand,stock,RAM)values("samsung",20,4),("apple",12,8),("nokia",10,2);

create table vegitables(type varchar(20),stock_details float, price_kg float);

insert into vegitables(type,stock_details,price_kg)values("potato",10,30),("onion",12,20),("chilli",16,20);

1) question: adding new column//
Ans: 

alter table grocery add column supplier varchar(20);
Query OK, 0 rows affected (0.015 sec)
Records: 0  Duplicates: 0  Warnings: 0

MariaDB [chaitanya]> select * from grocery;
+------+--------+-------+----------+
| s_id | p_name | price | supplier |
+------+--------+-------+----------+
|    1 | oil    |   130 | NULL     |
|    2 | suger  |    50 | NULL     |
|    3 | wheat  |    40 | NULL     |
+------+--------+-------+----------+ 

2) Question: drop column
Ans:
alter table grocery drop column supplier;
Query OK, 0 rows affected (0.013 sec)
Records: 0  Duplicates: 0  Warnings: 0

MariaDB [chaitanya]> select * from grocery;
+------+--------+-------+
| s_id | p_name | price |
+------+--------+-------+
|    1 | oil    |   130 |
|    2 | suger  |    50 |
|    3 | wheat  |    40 |
+------+--------+-------+

3)question: change table name// 
 Answer: 

MariaDB [chaitanya]> alter table mobiles rename to mobile_phones;
Query OK, 0 rows affected (0.011 sec)

MariaDB [chaitanya]> show tables;
+---------------------+
| Tables_in_chaitanya |
+---------------------+
| book                |
| customer1           |
| dept                |
| dept_details        |
| deptview            |
| electronics         |
| emp                 |
| emp_details         |
| employee            |
| employee_name       |
| emplyee             |
| garments            |
| grocery             |
| mobile_phones       |
| payments            |
| product1            |
| vegitables          |
+---------------------+

4)Question:  change column name//
Answer:
MariaDB [chaitanya]> alter table mobile_phones change column RAM INTERNAL varchar(20);
Query OK, 3 rows affected (0.040 sec)
Records: 3  Duplicates: 0  Warnings: 0

MariaDB [chaitanya]> select * from mobile_phones;
+---------+-------+----------+
| brand   | stock | INTERNAL |
+---------+-------+----------+
| samsung |    20 | 4        |
| apple   |    12 | 8        |
| nokia   |    10 | 2        |
+---------+-------+----------+

5) Question :delete table mobile_phone //// 
Answer: 

MariaDB [chaitanya]> delete from mobile_phones where stock=10;
Query OK, 1 row affected (0.003 sec)

MariaDB [chaitanya]> select * from mobile_phones;
+---------+-------+----------+
| brand   | stock | INTERNAL |
+---------+-------+----------+
| samsung |    20 | 4        |
| apple   |    12 | 8        |
+---------+-------+----------+

6)question:  truncate table///
Answer:
MariaDB [chaitanya]> truncate table course;
Query OK, 0 rows affected (0.014 sec)

MariaDB [chaitanya]> select * from course;
Empty set (0.000 sec).

7)Question: drop table///
Answer: 
drop table course;
MariaDB [chaitanya]> drop table course;
Query OK, 0 rows affected (0.006 sec)


8)Question:use logical OR operators//
Aswer:
MariaDB [chaitanya]> select * from mobile_phones where brand="samsung" or brand ="nokia";
+---------+-------+----------+
| brand   | stock | INTERNAL |
+---------+-------+----------+
| samsung |    20 | 4        |
| nokia   |    10 | 2        |
+---------+-------+----------+
9) use logical AND operators//
 
MariaDB [chaitanya]> select * from mobile_phones where brand="samsung" and stock =12;
Empty set (0.000 sec)

10)Question: give exapmle for  between keyword //
Answer:

MariaDB [chaitanya]> select * from grocery where price between 30 and 60;
+------+--------+-------+
| s_id | p_name | price |
+------+--------+-------+
|    2 | suger  |    50 |
|    3 | wheat  |    40 |
+------+--------+-------+

11) Que: Select table on ascending mode: 

ans: 
select * from mobile_phones order by stock asc;

MariaDB [chaitanya]> select * from mobile_phones order by stock asc;
+---------+-------+----------+
| brand   | stock | INTERNAL |
+---------+-------+----------+
| nokia   |    10 | 2        |
| apple   |    12 | 8        |
| samsung |    20 | 4        |
+---------+-------+----------+

12)Question : set order the mobile_phones by stock decrement:

Ans:  
MariaDB [chaitanya]> select * from mobile_phones order by stock desc;
+---------+-------+----------+
| brand   | stock | INTERNAL |
+---------+-------+----------+
| samsung |    20 | 4        |
| apple   |    12 | 8        |
| nokia   |    10 | 2        |
+---------+-------+----------+

13) Question:  set the limit for mobile_phones as 2: 
 
Ans: 
select * from mobile_phones limit 2;
MariaDB [chaitanya]> select * from mobile_phones limit 2;
+---------+-------+----------+
| brand   | stock | INTERNAL |
+---------+-------+----------+
| samsung |    20 | 4        |
| apple   |    12 | 8        |
+---------+-------+----------+

14) question : set book table order by limit
 Ans: 

MariaDB [chaitanya]> select * from book order by rating desc limit 5;
+------+---------+-------+-------+---------+--------+------------+
| bid  | bname   | price | pages | auther  | rating | pub_date   |
+------+---------+-------+-------+---------+--------+------------+
| 7000 | perl    | 43879 |   300 | abc     |      9 | NULL       |
| 4000 | oracle  |  2343 |   600 | brijani |      9 | 2022-08-04 |
| 2000 | python  | 34334 |   400 | pqr     |      8 | 2022-12-01 |
| 6000 | c sharp | 34568 |   800 | lmn     |      7 | NULL       |
| 3000 | sql     | 21321 |   500 | xyz     |      6 | 2022-03-05 |
+------+---------+-------+-------+---------+--------+------------+

15)Question: like keyword starts with character example: 
Answer:

MariaDB [chaitanya]> select * from mobile_phones where brand like's%';
+---------+-------+----------+
| brand   | stock | INTERNAL |
+---------+-------+----------+
| samsung |    20 | 4        |
+---------+-------+----------+

16)Question: make table for like keyword:
answer:

 MariaDB [chaitanya]> select * from mobile_phones where brand like'_a%';
+---------+-------+----------+
| brand   | stock | INTERNAL |
+---------+-------+----------+
| samsung |    20 | 4        |
+---------+-------+----------+

17) Question: Show null constraint exapmple.
Answer: 

MariaDB [chaitanya]> select * from mobile_phones where stock is null;
Empty set (0.002 sec)

18) Question: show concat from grocery coloumns
Answer: 

MariaDB [chaitanya]> select concat(s_id," " ,price)from grocery;
+-------------------------+
| concat(s_id," " ,price) |
+-------------------------+
| 1 130                   |
| 2 50                    |
| 3 40                    |
+-------------------------+

19) question: show current date  system date 
Answer : 

MariaDB [chaitanya]> select curdate();
+------------+
| curdate()  |
+------------+
| 2023-01-12 |

20) question: system date
answer:  

ariaDB [chaitanya]> select sysdate();
+---------------------+
| sysdate()           |
+---------------------+
| 2023-01-12 17:30:49 |
+---------------------+

21) question: show the table with group by clouse:
answer: 

MariaDB [chaitanya]> select max(stock) from mobile_phones group by stock;
+------------+
| max(stock) |
+------------+
|         10 |
|         12 |
|         20 |
+------------+

22) Question: make inner join with grocery table and electronics table
answer:  

MariaDB [chaitanya]> select grocery.s_id,grocery.price, electronics.s_id,electronics.stock from grocery inner join electronics on grocery.s_id=electronics.s_id;
+------+-------+------+-------+
| s_id | price | s_id | stock |
+------+-------+------+-------+
|    1 |   130 |    1 |    13 |
|    2 |    50 |    2 |    22 |
|    3 |    40 |    3 |    16 |
+------+-------+------+-------+

23) Question: make left join with grocery table and electronics table 

Answer : 
MariaDB [chaitanya]> select grocery.s_id,grocery.price, electronics.s_id,electronics.stock from grocery left join electronics on grocery.s_id=electronics.s_id;
+------+-------+------+-------+
| s_id | price | s_id | stock |
+------+-------+------+-------+
|    1 |   130 |    1 |    13 |
|    2 |    50 |    2 |    22 |
|    3 |    40 |    3 |    16 |
+------+-------+------+-------+

24) Question: make right join with grocery table and electronics table // Right join //
answer : 

select grocery.s_id,grocery.price, electronics.s_id,electronics.stock from grocery right join electronics on grocery.s_id=electronics.s_id;
+------+-------+------+-------+
| s_id | price | s_id | stock |
+------+-------+------+-------+
|    1 |   130 |    1 |    13 |
|    2 |    50 |    2 |    22 |
|    3 |    40 |    3 |    16 |
+------+-------+------+-------+

25)Question: make cross join with grocery table and electronics table cross join//
answer : 

MariaDB [chaitanya]> select * from grocery,electronics;
+------+--------+-------+------+---------+-------+------+
| s_id | p_name | price | p_id | product | stock | s_id |
+------+--------+-------+------+---------+-------+------+
|    1 | oil    |   130 |  101 | TV      |    13 |    1 |
|    2 | suger  |    50 |  101 | TV      |    13 |    1 |
|    3 | wheat  |    40 |  101 | TV      |    13 |    1 |
|    1 | oil    |   130 |  102 | AC      |    22 |    2 |
|    2 | suger  |    50 |  102 | AC      |    22 |    2 |
|    3 | wheat  |    40 |  102 | AC      |    22 |    2 |
|    1 | oil    |   130 |  107 | iron    |    16 |    3 |
|    2 | suger  |    50 |  107 | iron    |    16 |    3 |
|    3 | wheat  |    40 |  107 | iron    |    16 |    3 |
+------+--------+-------+------+---------+-------+------+

26)Question: make self join with grocery table and electronics table // self join// 
answer: 

MariaDB [chaitanya]> select A.s_id,B.p_name from grocery AS A,grocery AS B where A.s_id=B.s_id;
+------+--------+
| s_id | p_name |
+------+--------+
|    1 | oil    |
|    2 | suger  |
|    3 | wheat  |
+------+--------+

subqueries// 

27) Write query to find the price of product whoes price is greater than the price of product whose s_id is =3?

Answer : select s_id,price from grocery where price>(select price from grocery where s_id=3);


MariaDB [chaitanya]> select s_id,price from grocery where price>(select price from grocery where s_id=3);
+------+-------+
| s_id | price |
+------+-------+
|    1 |   130 |
|    2 |    50 |
+------+-------+


28) Write query to find the price of product whoes price is less than the price of product whose s_id is =3?

MariaDB [chaitanya]> select s_id,price from grocery where price<(select price from grocery where s_id=3);


29)  Write a query to find from all products which has highest price?

Ans: MariaDB [chaitanya]> select * from grocery where price=(select max(price)from grocery);
+------+--------+-------+
| s_id | p_name | price |
+------+--------+-------+
|    1 | oil    |   130 |
+------+--------+-------+

30) Write query to find from electronics whose stock is equal to stock of at least one stock in p_id =102?

MariaDB [chaitanya]> select * from electronics where stock in (select stock where p_id=102);
+------+---------+-------+------+
| p_id | product | stock | s_id |
+------+---------+-------+------+
|  102 | AC      |    22 |    2 |
+------+---------+-------+------+

3) alter table garments change column materail materail_1 varchar(20);
Query OK, 3 rows affected (0.061 sec)
Records: 3  Duplicates: 0  Warnings: 0

MariaDB [chaitanya]> select * from garments;
+------+-------------+------------+------+
| g_id | brand       | materail_1 | p_id |
+------+-------------+------------+------+
|  201 | raymond     | jute       |  101 |
|  202 | cotton_king | cotton     |  102 |
|  203 | siyaram     | leather    |  107 |
+------+-------------+------------+------+

4) alter table grocery rename to grocery_1;

2) select p_name,price from grocery where grocery =(select p_name from grocery where p_name=oil);
 

select product, stock from electronics (select p_id from electronics where product=102); 
