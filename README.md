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

## Deliverables
The goal of this lab is to design and interact with a MySQL database that meets the needs of a typical application.

Your goal is to:
- Define a schema that adheres to the requirements of the application.
- Implement the schema in MySQL.
- Execute and capture the results of specific queries.

When you are done, please upload the following:
- Schema diagram
- ER diagram including attributes and data types
- Queries
- Query result screenshots

## Instructions

### Part 1: Database Schema Design
Your client wants your database to manage the following information for a book store:

**Book**
- `title` -- Title of the book
- `author` -- Author of the book
- `publicationYear` -- Year of publication
- `genre` -- Genre of the book
- `price` -- Price of the book

**Customer**
- `firstName` -- First name of the customer
- `lastName` -- Last name of the customer
- `email` -- Email address of the customer
- `phoneNumber` -- Phone number of the customer

**Order**
- `orderNumber` -- Order number
- `orderDate` -- Date of the order
- `customerID` -- ID of the customer who placed the order
- `totalAmount` -- Total amount of the order

**OrderDetail**
- `orderNumber` -- Order number
- `bookTitle` -- Title of the book ordered
- `quantity` -- Quantity of the book ordered

Create an ER diagram for the above schema and implement it in MySQL.

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
