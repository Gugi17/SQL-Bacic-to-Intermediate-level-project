# SQL-Bacic-to-Intermediate-level-project
SQL project on Gomato data analysis 

Tool use- **MY SQL**


create database if not exists gomato

use gomato

create table goldusers_signup(userid integer,
gold_signup_date date);

INSERT INTO goldusers_signup(userid,gold_signup_date) 
 VALUES (1,'2017-09-22'),
(3,'2017-04-21');

CREATE TABLE users(userid integer,
signup_date date);

INSERT INTO users(userid,signup_date) 
 VALUES (1,'2014-02-09'),
(2,'2015-01-15'),
(3,'2014-11-04');

CREATE TABLE sales(userid integer,
created_date date,
product_id integer); 

INSERT INTO sales(userid,created_date,product_id) 
 VALUES (1,'2017-04-19',2),
(3,'2019-12-18',1),
(2,'2020-07-20',3),
(1,'2019-10-23',2),
(1,'2018-03-19',3),
(3,'2016-12-20',2),
(1,'2016-11-09',1),
(1,'2016-05-20',3),
(2,'2017-09-24',1),
(1,'2017-03-11',2),
(1,'2016-03-11',1),
(3,'2016-11-10',1),
(3,'2017-12-07',2),
(3,'2016-12-15',2),
(2,'2017-11-08',2),
(2,'2018-09-10',3);

CREATE TABLE product(product_id integer,
product_name text,
price integer); 

INSERT INTO product(product_id,product_name,price) 
 VALUES
(1,'p1',980),
(2,'p2',870),
(3,'p3',330);

select * from goldusers_signup;
select * from product;
select * from sales;
select * from users;


---1st Q- what is total amount each customer spent on zomato ?

select userid, sum(price) as total_amount_spent 
from sales
inner join product on 
sales.product_id=product.product_id
group by userid
order by userid;

---2nd Q- How many days has each customer visited zomato?

select userid, 
count(distinct created_date) as total_visited_day 
from sales
group by userid
order by userid;


3rd Q--- what is most purchased item on menu & how many times was it purchased by all customers ?

select product_id, count(product_id)as highest_purchased_item
from sales
group by product_id
limit 1;
