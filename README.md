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

### Exercise 1: Installing and Connecting to MySQL

Go to Workbench lesson, connect and install MySQL Workbench in your computer

### Exercise 2: Create an ER diagram

To store the collected information, you need to create an organized structure. Tables are the foundation for storing data efficiently and in an orderly manner.

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
```
Create an ER diagram: [dbdiagram](https://dbdiagram.io/home).

### Exercise 3: Create Tables

You need to create two tables: `Missions` and `Commanders`.

1. The table should have the following columns:
   - `mission_id` (Primary Key, Integer)
   - `mission_name` (Variable Character, 50 characters)
   - `start_date` (Date)
   - `end_date` (Date)
   - `status` (Enum: 'Planned', 'Ongoing', 'Completed')

2. The table should have the following columns:
   - `commander_id` (Primary Key, Integer)
   - `commander_name` (Variable Character, 50 characters)
   - `rank` (Variable Character, 20 characters)
   - `assigned_mission` (Foreign Key referencing mission_id in Missions table)


![happy_coding](https://user-images.githubusercontent.com/970858/63899010-c23fc480-c9ea-11e9-84a2-542907e42362.png)
