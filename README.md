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


## Story:
You have been recruited by the Rebel Alliance as a data specialist. Your mission is to design and interact with a MySQL database that meets the needs of the Rebel operations. This database will store crucial intelligence about the Empire and the galaxy, helping the Rebellion strategize and execute their plans.

## Objectives:
- Define a schema that adheres to the operational requirements of the Rebel Alliance.
- Implement the schema in MySQL.
- Execute and capture the results of specific queries to gather intelligence.

## Deliverables:
When you are done, please upload the following:
- ER diagram including attributes and data types
- Queries in markdown or Query result screenshots

## Iteration 1: Installing and Connecting to MySQL

 1. Go to Workbench lesson and find the command to install mysql
 2. Install MySQL Workbench on your computer.
 3. Open MySQL Workbench and connect to your MySQL server.

## Iteration 2: Create an ER diagram

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
    birth_date VARCHAR(10),
);
```
Create an ER diagram: [dbdiagram](https://dbdiagram.io/hCharome).

## Iteration 3: Create Tables

### 3.1 Create in MySQLWorkbench a database called Rebel_Alliance
### 3.2 Selecting the Database

```sql 
USE my_database;
```
### 3.3 Add Previous tables : Planets, Ships, Characters

### 3.4 Add these two new tables  

1. The table should have the following columns:
   - `mission_id` (Primary Key, Integer)
   - `mission_name` (Variable Character, 50 characters)
   - `start_date` (Date)
   - `end_date` (Date)
   - `status` (Enum: 'Planned', 'Ongoing', 'Completed')

2. The table should have the following columns:
   - `commander_id` (Primary Key, Integer)
   - `commander_name` (Variable Character, 50 characters)
   - `status` (Variable Character, 20 characters)
   - `assigned_mission` (Integer)


## Iteration 4: Insert Data  

The Rebel Alliance has gathered vital information about planets, ships, characters, and missions. Your task is to organize and insert this data into the respective tables in the database. This will help the Alliance plan their strategies and execute their missions effectively.

<img src="https://github.com/user-attachments/assets/011c8de0-5e2e-42d8-a010-d460340bbb32" alt="Descripción de la imagen" width="800" >



### Tabla Planets

| planet_id | planet_name | region      | population | discovered_date |
|-----------|-------------|-------------|------------|-----------------|
| 1         | Tatooine    | Outer Rim   | 200000     | 1977-05-25      |
| 2         | Alderaan    | Core Worlds | 2000000000 | 1977-05-25      |
| 3         | Hoth        | Outer Rim   | 0          | 1980-05-21      |
| 4         | Endor       | Outer Rim   | 30000      | 1983-05-25      |
| 5         | Coruscant   | Core Worlds | 1000000000 | 1999-05-19      |

### Tabla Ships

| ship_id | ship_name      | ship_type    | capacity | in_service                   |
|---------|----------------|--------------|----------|------------------------------|
| 1       | Millennium Falcon | Freighter   | 6      | Independent                  |
| 2       | X-Wing         | Starfighter  | 1        | Rebel Alliance               |
| 3       | TIE Fighter    | Starfighter  | 1        | Galactic Empire              |
| 4       | Star Destroyer | Capital Ship | 47000    | Galactic Empire              |
| 5       | Slave I        | Starfighter  | 1        | Independent                  |

### Tabla Characters

| character_id | character_name  | affiliation      | home_planet | birth_date  |
|--------------|-----------------|------------------|-------------|-------------|
| 1            | Luke Skywalker  | Rebel Alliance   | Tatooine    | 19BBY       |
| 2            | Princess Leia   | Rebel Alliance   | Alderaan    | 19BBY       |
| 3            | Darth Vader     | Uknow  | Tatooine    | 41BBY       |
| 4            | Han Solo        | Rebel Alliance   | Corellia    | 29BBY       |
| 5            | Boba Fett       | Independent      | Kamino      | 32BBY       |

### Tabla Missions

| mission_id | mission_name            | start_date | end_date   | status     |
|------------|-------------------------|------------|------------|------------|
| 1          | Battle of Yavin         | 1977-05-25 | 1977-05-25 | Completed  |
| 2          | Assault on Hoth         | 1980-05-21 | 1980-05-21 | Completed  |
| 3          | Rescue of Han Solo      | 1983-05-25 | 1983-05-25 | Completed  |
| 4          | Battle of Endor         | 1983-05-25 | 1983-05-25 | Completed  |
| 5          | First Death Star Attack | 1977-05-25 | 1977-05-25 | Completed  |

### Tabla Commanders

| commander_id | commander_name | status          | assigned_mission |
|--------------|----------------|---------------|------------------|
| 1            | General Dodonna| General       | 1                |
| 2            | General Rieekan| General       | 2                |
| 3            | Lando Calrissian| General      | 3                |
| 4            | Admiral Ackbar | Admiral       | 4                |
| 5            | Darth Vader    | Sith Lord     | 5                |


## Iteration 5: Assist C-3PO with Critical Data Retrieval

C-3PO, the loyal protocol droid, has been assigned to gather and organize this information, but he needs your expertise in SQL. By helping C-3PO retrieve the necessary data, you will play a vital role in supporting the Rebel Alliance's efforts.

### 5.1 Complete List of Planet Names
 C-3PO needs a complete list of all known planet names to update the Galactic Atlas.
### 5.2 Fleet Inventory
C-3PO must verify the fleet inventory by retrieving the names and types of all ships in the database.
### 5.3 Characters and Their Affiliations
C-3PO needs a list of all name characters involved and their affiliation.
### 5.4 Leadership Structure Report
C-3PO is tasked with compiling a report on the leadership structure of the Rebel Alliance and the Galactic Empire. Retrieve the names and status of all commanders.

By completing these queries, you will help C-3PO gather the necessary data to assist the Rebel Alliance in their strategic planning and operations against the Galactic Empire. Your contribution is crucial for the success of the Rebellion. May the Force be with you!

<img src="https://github.com/user-attachments/assets/d27b2f23-e0df-4fb6-9512-3d203690ed0a" alt="Descripción de la imagen" width="800" >

## Iteration 6: Updating and Deleting outdated Data 

Princess Leia, a key leader of the Rebel Alliance, has identified some outdated and incorrect data in the Rebel Alliance database. She needs your help to update and delete certain records to ensure the accuracy of their intelligence. Your expertise in SQL is crucial for making these necessary changes.

### 6.1 Update Ship Status
The Millennium Falcon, previously classified as 'Independent', is now officially part of the Rebel Alliance. Update the service status to 'Rebel Alliance'.

### 6.2 Correct Character Affiliation
Princess Leia discovered that Darth Vader's affiliation was recorded incorrectly. Update the affiliation to 'Galactic Empire'.

### 6.3 Delete Obsolete Mission
The record of an obsolete mission, "First Death Star Attack", should be deleted from the missions database.

### 6.4 Remove Commanders Table
 Princess Leia has determined that the `Commanders` table should be removed from the current database to secure the information.


## BONUS - **Advanced Rebelds Queries**

### - Find all characters who are affiliated with the Rebel Alliance and were born before 20BBY.

### - Retrieve the names and capacities of all ships that are either 'Freighter' or 'Capital Ship' type and have a capacity greater than 1000.

### - Increase the population of all planets in the 'Core Worlds' region by 10%.

### - Remove all ships that are not in service with either the 'Rebel Alliance' or the 'Galactic Empire'.

Congratulations on completing the Star Wars SQL Exercises! Your work has been instrumental in aiding the Rebel Alliance. By helping to organize, update, and secure vital data, you have played a crucial role in the ongoing fight against the Galactic Empire. Your SQL skills have not only improved but have also contributed significantly to the success of the Rebellion.

May the knowledge you have gained continue to serve you well in all your future endeavors. Remember, the Force will be with you, always.

<img src="https://github.com/user-attachments/assets/ce3a1d3a-c929-40e8-abb4-a930936d635e" alt="Descripción de la imagen" width="800" >

## Submission

Upon completion, run the following commands:

```
$ git add .
$ git commit -m "done"
$ git push origin main
```

Then create a Pull Request!!

![happy_coding](https://user-images.githubusercontent.com/970858/63899010-c23fc480-c9ea-11e9-84a2-542907e42362.png)
