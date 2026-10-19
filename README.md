# Train Ticket Reservation System

A Java-based web application for searching trains, checking availability and fares, and managing ticket reservations.

**Maintainer:** Manjush Premkumar  
**Technologies:** Java, Servlets, JDBC, Oracle SQL, HTML, CSS, Bootstrap

---

## Project Overview

The Train Ticket Reservation System is a web application designed to simplify train information searches and ticket reservation management.

Users can register, log in, search for trains between stations, check fares, book tickets, and view their booking history. Administrators can manage train information through dedicated administrative functionality.

This project is being used to study Java web development, database connectivity, and the architecture of web applications.

## Features

### User Features

- User registration and login
- View available trains
- Search for trains between stations
- Check train availability
- View train schedules and fares
- Book train tickets
- View booking details
- Access booking history
- View and update profile information
- Change password
- Log out

### Administrator Features

- Administrator login
- Add new trains
- View available trains
- Update train information
- Remove or cancel trains
- Manage profile information
- Log out

### Additional Features

The original project also advertises payment processing and ticket booking history. Refer to the implementation to verify the functionality of each feature.

---

## Technology Stack

### Frontend
- HTML
- CSS
- Bootstrap

### Backend
- Java (J2EE / Java EE)
- Java Servlets
- JDBC

### Database
- Oracle SQL

### Development Tools
- Git
- Java Development Kit (JDK)
- Eclipse IDE for Enterprise Java and Web Developers
- Apache Maven
- Apache Tomcat
- Oracle SQL Developer or SQL*Plus

> Note: This project uses Java Servlets and JDBC. It does not use Spring Boot.

---

## Application Architecture

The application follows a traditional Java web application architecture.

```text
User
  |
  v
Frontend (HTML, CSS, Bootstrap)
  |
  v
Java Servlets
  |
  v
Application Logic
  |
  v
JDBC
  |
  v
Oracle Database
```

The frontend provides the user interface. Java Servlets handle web requests, application logic processes operations, and JDBC enables communication with the Oracle database.

---

## Database Structure

The database setup described in the original project contains four tables.

| Table | Purpose |
|---|---|
| `CUSTOMER` | Stores customer information |
| `ADMIN` | Stores administrator information |
| `TRAIN` | Stores train details, routes, available seats, and fares |
| `HISTORY` | Stores ticket booking information |

The `HISTORY` table includes booking identifiers, customer references, train numbers, travel dates, source and destination stations, seat counts, and booking amounts.

### Database Setup

The original setup instructions use Oracle SQL*Plus or Oracle SQL Developer.

**Important:** The SQL below is adapted from the original project. Use a local development database and avoid granting unnecessary administrative privileges to application accounts.

#### Step 1: Create the database user

Connect to Oracle using an account authorized to create users.

```sql
CREATE USER RESERVATION IDENTIFIED BY "ChooseYourOwnPassword";
GRANT CREATE SESSION, CREATE TABLE TO RESERVATION;
```

Depending on your Oracle version and configuration, additional privileges may be required.

#### Step 2: Connect as the reservation user

```sql
CONNECT RESERVATION/"ChooseYourOwnPassword";
```

#### Step 3: Create the tables

```sql
CREATE TABLE CUSTOMER (
    MAILID VARCHAR2(40) PRIMARY KEY,
    PWORD VARCHAR2(20) NOT NULL,
    FNAME VARCHAR2(20) NOT NULL,
    LNAME VARCHAR2(20),
    ADDR VARCHAR2(100),
    PHNO NUMBER(12) NOT NULL
);

CREATE TABLE ADMIN (
    MAILID VARCHAR2(40) PRIMARY KEY,
    PWORD VARCHAR2(20) NOT NULL,
    FNAME VARCHAR2(20) NOT NULL,
    LNAME VARCHAR2(20),
    ADDR VARCHAR2(100),
    PHNO NUMBER(12) NOT NULL
);

CREATE TABLE TRAIN (
    TR_NO NUMBER(10) PRIMARY KEY,
    TR_NAME VARCHAR2(70) NOT NULL,
    FROM_STN VARCHAR2(20) NOT NULL,
    TO_STN VARCHAR2(20) NOT NULL,
    SEATS NUMBER(4) NOT NULL,
    FARE NUMBER(6,2) NOT NULL
);

CREATE TABLE HISTORY (
    TRANSID VARCHAR2(36) PRIMARY KEY,
    MAILID VARCHAR2(40)
        REFERENCES CUSTOMER(MAILID),
    TR_NO NUMBER(10),
    "DATE" DATE,
    FROM_STN VARCHAR2(20) NOT NULL,
    TO_STN VARCHAR2(20) NOT NULL,
    SEATS NUMBER(3) NOT NULL,
    AMOUNT NUMBER(8,2) NOT NULL
);
```

> **Security note:** The schema above reflects the original project's design. Before using the application beyond local learning, review its password-storage implementation and replace plaintext password storage with a secure password-hashing approach.

#### Step 4: Verify the tables

```sql
SELECT * FROM CUSTOMER;
SELECT * FROM ADMIN;
SELECT * FROM TRAIN;
SELECT * FROM HISTORY;
```

The original repository includes sample data in its database setup instructions. Consult the original README if you need those specific sample records.

---

## Installation and Setup

The original project documentation describes running the application through Eclipse and Apache Tomcat.

### Prerequisites

Install the following software as required by the project:

- Git
- A compatible JDK
- Eclipse IDE for Enterprise Java and Web Developers
- Apache Maven
- A compatible Apache Tomcat version
- Oracle Database
- Oracle SQL Developer or SQL*Plus

The original setup guide targets an older Java web application environment. Compatibility adjustments may be necessary with newer Java and Tomcat versions.

### Step 1: Clone the repository

```bash
git clone https://github.com/manjush007/-Train-Ticket-Reservation-System.git
```

### Step 2: Enter the project directory

```bash
cd -Train-Ticket-Reservation-System
```

If the directory name on your computer differs, use the actual directory name.

### Step 3: Build with Maven

```bash
mvn clean install
```

Resolve any dependency or compatibility errors before continuing.

### Step 4: Configure the database

Create the Oracle database tables and configure the application's database connection settings according to the source code.

Do not commit real database credentials to GitHub.

### Step 5: Configure Tomcat

Import the project into Eclipse as an existing Maven project. Configure a compatible Tomcat server and deploy the web application.

The original documentation uses port `8083` and the context path `/trainbook/`.

If your local configuration matches those settings, the application may be accessible at:

```text
http://localhost:8083/trainbook/
```

This address works only when the application has been configured and started successfully.

---

## Screenshots

The original project includes screenshots of several application pages, including:

- Login page
- User registration
- User profile
- Train search
- Available trains
- Ticket booking
- Booking details
- Booking history
- Fare enquiry
- Password changes
- Administrator train management

Refer to the original repository's `Screenshots` directory for the available images.

---

## Learning Objectives

This repository is being used to explore the following concepts:

- Core Java and object-oriented programming
- Java Servlets and HTTP request handling
- JDBC and relational database connectivity
- SQL queries and database relationships
- CRUD operations
- Traditional Java web application architecture
- Maven-based project builds
- Git and GitHub workflows

The goal is to build a deeper understanding of how Java web applications are structured and how their components interact.

---

## Maintainer

**Manjush Premkumar**

This repository is maintained for learning, experimentation, and documenting improvements to Java web application development.
