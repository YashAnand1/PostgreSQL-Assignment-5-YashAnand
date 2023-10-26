<div align="center">


<!-- add technical charcha logo postgres session 3 -->
# PostgresSQL: Assignment 5        
### — A Task Documentation by Yash Anand—    

_____________________________________________________________________________________                        

## Contents
</div>

- [PostgresSQL: Assignment 5](#postgressql-assignment-5)
    - [— A Task Documentation by Yash Anand—](#-a-task-documentation-by-yash-anand)
  - [Contents](#contents)
- [**Overview**](#overview)
  - [**Prerequisites**](#prerequisites)
  - [**Task 1: Creation Of Database**](#task-1-creation-of-database)
  - [**Conclusion**](#conclusion)
 
_____________________________________________________________________________________      
  
<div align="center">
   
## **Prerequisites**
</div>

Before being able to start working on the Assignment-5, I needed to ensure that Docker had been installed on my system. In order to do so, I first installed Docker from its [official documentation](https://docs.docker.com/engine/install/ubuntu/) and gained a better understanding of Docker using [this tutorial](https://www.youtube.com/watch?v=pg19Z8LL06w). Once I had done this all, I was ready to start working on this assignment.

--------
<div align="center">

## **Task 1: Creation Of Database**
</div>

> Set up a container for Database 1 and assign a port.   

As per the first task, we were to create a container for a PostgreSQL database, while defining its ports. As discussed in the 'PostgreSQL Session 5', the database that I created was based on a hypothetical data from a grocery store. The data was inserted into this database to keep the data as realistic as possible.

In order to create such a container, the fllowing steps were utilised by me for creating the first database:        

1 Containerisation & Assigning Ports 
```
docker run -d -p 5432:5432 --name grocery_db1 -e POSTGRES_PASSWORD=a postgres
```
 Output:
 <div align="center">

 ![image](https://i.imgur.com/IOg7xj3.png)
 </div>
To ensure that the container had been created, I also ran the `docker ps` command for listing the running containers. 

________________
2 Creating A Database

Before being able to create a database, I needed to first enter into the previously created Postgres container. However, to create create a database, it was also required to enter start the psql interactive terminal for communicating with the PostgreSQL. To do this, I ran the following command: 
```
docker exec -it grocery_db1 psql -U postgres
```

Once I had entered into the container and started the psql terminal, I created the first database for filling it up with the sample data of a grocery store. Therefore, the name of the database was set as such in the following query:  
```
CREATE DATABASE grocery_db1; 
```

Once the database had been created, I entered into it using the `\c grocery_db1` command, which would allow me to later modify the database in the next steps. 
 Output:
 <div align="center">

 ![image](https://i.imgur.com/sInE8nw.png)
 </div>

______________

3 Table Creation

Given I had entered into the `grocery_db1`, I needed to populate the data. But before that, I first created a table called `grocery_register` and then filled it up with hypothetical data that could be used for keeping track of transactions made with customers using a grocery register. For this, I wrote the following query: 
```
CREATE TABLE grocery_register (
customer_id SERIAL PRIMARY KEY,
product_name VARCHAR,
date_bought_on DATE,
product_cost INT,
price_paid INT,
price_due ONT,
phone_no BIGINIT,
address VARCHAR,
customer_name VARCHAR);
```
Once the `CREATE TABLE` output had been displayed after running the above query, I decided to ensure the table's creation by running the `\dt` command. The output of running the query and this command was: 
 Output:
 <div align="center">

 ![image](https://i.imgur.com/j69IPgB.png)
 </div>
______________

## 1.1 Populating Data

> Populate Database 1 with sample data, such as
information for a hospital, school, and college.

Given that the `grocery_register` table had been successfuly created, I could now work on populating it with some sample data. In order to do so, I ran the following query:

```
INSERT INTO grocery_register
(product_name, date_bought_on, product_cost, price_paid, price_due, phone_no, address, customer_name)
VALUES
('Puffcorn Chips', '2023-10-23', 10, 10, 0, 9311670656, 'A-205, VV Appt., Sec-6, Vasundhara, Ghaziabad', 'Yash Anand') 
('Coca-Cola 50l', '2023-10-22', 50, 25, 25, 7837728518, 'B-149, KNA, Sec-63, Noida', 'Shobhit Kumar');
```
 Output:
 <div align="center">

 ![image](https://i.imgur.com/nf58HKO.png)
 </div>
 
In order to ensure that the data had been successfuly entered into the table, even though `INSERT 0 2` meant that it had, I ran the following query for retrieving all the data included inside the `grocery_register` table:
```
SELECT * FROM grocery_register;
```
Output:

 <div align="center">

 ![image](https://i.imgur.com/qf4zkTd.png)
 </div>
 Given that the table displayed as the result of the above query contained all the data that had been populated in it earlier, I concluded that the first task had therefore been completed.
_____________________________

<div align="center">

## **Task 2: **
</div>

> Set up a container for Database 1 and assign a port.   



  <div align="center">

## **Conclusion**
</div>

After the completion of these 4 tasks, which greatly depended on building relationships between tables, I was able to learn and understand the concept of primary keys, foreign keys, constraints, joins and alters. Through this document, I was also able to demonstrate and perform the assigned tasks, which helped me gain a lot of practical understanding of PostgreSQL and SQL.

--------
