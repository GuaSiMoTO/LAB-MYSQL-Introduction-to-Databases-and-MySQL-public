![](https://user-images.githubusercontent.com/970858/63474771-d6734700-c469-11e9-83bb-9429da563909.png)

# LAB-MYSQL-Introduction-to-Databases-and-MySQL

## Introduction
**Note:** This can be a pair programming activity or done independently.

At Reboot Academy, we aim to equip you with practical skills in managing databases. In this lab, we will be exploring MySQL, a popular relational database management system, to understand its role in data management and learn how to use its fundamental operations effectively.

**Ready?**

## Requirements
- Learn how to fork this repo.
- Clone this repo into your `code/labs` folder.
- Have MySQL installed.
- Have MySQL Workbench installed or any other MySQL client.

<img src="intro.gif" alt="Descripción de la imagen" width="800" >


### Story:
You have been recruited by the Rebel Alliance as a data specialist. Your mission is to design and interact with a MySQL database that meets the needs of the Rebel operations. This database will store crucial intelligence about the Empire and the galaxy, helping the Rebellion strategize and execute their plans.

### Objectives:
- Define a schema that adheres to the operational requirements of the Rebel Alliance.
- Implement the schema in MySQL.
- Execute and capture the results of specific queries to gather intelligence.

### Deliverables:
When you are done, please upload the following:
- Schema diagram
- ER diagram including attributes and data types
- Queries
- Query result screenshots

  
## Instructions

# Lab 1: Introduction to SQL with a Star Wars Theme

### Star Wars Context:
In a galaxy divided by war, the Rebel Alliance fights against the oppressive Galactic Empire. The heroes of the Rebellion, Luke Skywalker, Princess Leia, and Han Solo, face off against the dark forces led by Darth Vader and Emperor Palpatine in an epic battle for freedom and justice.

### Story:
You have been recruited by the Rebel Alliance as a data specialist. Your initial mission is to organize and structure the intelligence gathered about the Empire, crucial information for Rebel operations. The data includes planets, ships, and key characters, vital for the Rebellion's strategy.

### Exercise 1: Create Tables
**Situation:**
To store the collected information, you need to create an organized structure. Tables are the foundation for storing data efficiently and in an orderly manner.

**Task:**
Create a database with tables to store information about planets, ships, and key characters, including date, enum, and set data types.

```sql
CREATE TABLE Planets (
    planet_id INT PRIMARY KEY,
    planet_name VARCHAR(50),
    region VARCHAR(50),
    population BIGINT,
    discovered_date DATE
);

CREATE TABLE Ships (
    ship_id INT PRIMARY KEY,
    ship_name VARCHAR(50),
    ship_type ENUM('Freighter', 'Starfighter', 'Capital Ship'),
    capacity INT,
    in_service SET('Rebel Alliance', 'Galactic Empire', 'Independent')
);

CREATE TABLE Characters (
    character_id INT PRIMARY KEY,
    character_name VARCHAR(50),
    affiliation VARCHAR(50),
    home_planet VARCHAR(50),
    birth_date DATE
);

Create an ER diagram: [dbdiagram](https://dbdiagram.io/home).

### Part 2: Installing and Connecting to MySQL
**Connection:**
Connect to your MySQL database using MySQL Workbench or the command-line interface (CLI).

### Part 3: Schema Implementation and Queries
**Schema Creation:**

Create the database and tables based on your ER diagram.
```sql
CREATE DATABASE BookStore;
USE BookStore;

CREATE TABLE Book (
    title VARCHAR(255) NOT NULL,
    author VARCHAR(255),
    publicationYear YEAR,
    genre VARCHAR(100),
    price DECIMAL(10, 2),
    PRIMARY KEY (title)
);

CREATE TABLE Customer (
    customerID INT AUTO_INCREMENT,
    firstName VARCHAR(255),
    lastName VARCHAR(255),
    email VARCHAR(255),
    phoneNumber VARCHAR(15),
    PRIMARY KEY (customerID)
);

CREATE TABLE `Order` (
    orderNumber INT AUTO_INCREMENT,
    orderDate DATE,
    customerID INT,
    totalAmount DECIMAL(10, 2),
    PRIMARY KEY (orderNumber),
    FOREIGN KEY (customerID) REFERENCES Customer(customerID)
);

CREATE TABLE OrderDetail (
    orderNumber INT,
    bookTitle VARCHAR(255),
    quantity INT,
    PRIMARY KEY (orderNumber, bookTitle),
    FOREIGN KEY (orderNumber) REFERENCES `Order`(orderNumber),
    FOREIGN KEY (bookTitle) REFERENCES Book(title)
);
![happy_coding](https://user-images.githubusercontent.com/970858/63899010-c23fc480-c9ea-11e9-84a2-542907e42362.png)
