# Car Rental System Database Schema

## Overview
This repository contains the SQL schema and initial data for a **Car Rental System**. The database consists of multiple tables, each representing a different entity, such as users, admins, cars, bookings, and sales. This README provides a structured breakdown of the database schema, including the purpose and structure of each table.

## Database Tables

### 1. Admin Table
**Purpose:** Stores administrator details for managing the car rental system.

**Schema:**
```sql
CREATE TABLE Admin (
    id INT,
    firstname VARCHAR(100),
    lastname VARCHAR(100),
    username VARCHAR(100),
    email VARCHAR(100),
    role VARCHAR(100)
);
```

**Sample Data:**
```sql
INSERT INTO Admin VALUES (1, 'raja', 'mohan', 'rajamohan', 'raja@', 'admin1');
INSERT INTO Admin VALUES (2, 'hema', 'shulka', 'hemashulka', 'hema@', 'admin2');
```

---

### 2. Inquiry Table
**Purpose:** Stores customer inquiries related to cars and rental services.

**Schema:**
```sql
CREATE TABLE Inquiry (
    id INT,
    name VARCHAR(100),
    email VARCHAR(100),
    message VARCHAR(100)
);
```

**Sample Data:**
```sql
INSERT INTO Inquiry VALUES (1, 'Ram', 'ram@', 'check car details');
```

---

### 3. User Table
**Purpose:** Stores user details who rent or inquire about cars.

**Schema:**
```sql
CREATE TABLE USER (
    id INT,
    name VARCHAR(100),
    address VARCHAR(100),
    contact VARCHAR(100),
    email VARCHAR(100),
    age VARCHAR(100),
    gender VARCHAR(100),
    detail VARCHAR(100)
);
```

**Sample Data:**
```sql
INSERT INTO USER VALUES (2, 'ramtu', 'chennai', '9425132545', 'rmto@','18','male','details of color');
```

---

### 4. Sale Cars Table
**Purpose:** Stores details of cars available for sale along with seller information.

**Schema:**
```sql
CREATE TABLE sale_cars (
    id INT,
    salesname VARCHAR(100),
    carprice VARCHAR(100),
    carspecialisation VARCHAR(100),
    saler_contact VARCHAR(100) -- Fixed syntax error in column name
);
```

**Sample Data:**
```sql
INSERT INTO sale_cars VALUES (1, 'tanga', '5000000', 'engine', '756456484');
INSERT INTO sale_cars VALUES (2, 'vamba', '7000000', 'color', '4782498242');
```

---

### 5. Cars Table
**Purpose:** Stores details of cars available for rent.

**Schema:**
```sql
CREATE TABLE cars (
    id INT,
    car VARCHAR(100),
    carmodel VARCHAR(100),
    mileage VARCHAR(100),
    passenger VARCHAR(100),
    rent VARCHAR(100)
);
```

**Sample Data:**
```sql
INSERT INTO cars VALUES (1, 'punch', 'latest', '25', '4', '45000');
INSERT INTO cars VALUES (2, 'celerio', 'latest', '22', '4', '50000');
```

---

### 6. Car Booking Table
**Purpose:** Stores booking details for rented cars.

**Schema:**
```sql
CREATE TABLE carbooking (
    id INT,
    carid INT,
    name VARCHAR(100),
    contact VARCHAR(100),
    email VARCHAR(100),
    model VARCHAR(100)
);
```

**Sample Data:**
```sql
INSERT INTO carbooking VALUES (1, 1, 'toto', '7894561235', 'toto@', 'latest');
INSERT INTO carbooking VALUES (2, 2, 'morto', '7564893215', 'morto@', 'latest');
```

---

### 7. Tripped History Table
**Purpose:** Stores historical trip data of users.

**Schema:**
```sql
CREATE TABLE trippedhistory (
    id INT,
    firstname VARCHAR(100),
    lastname VARCHAR(100),
    role VARCHAR(100)
);
```

**Issues & Fixes:**
- There is an incorrect duplicate insertion of `cars` data in the original script.

---

## Corrections & Enhancements

1. **Fixed Column Name Error in `sale_cars` Table:**
   - The column name `saler contact` had a space, which is invalid. Changed it to `saler_contact`.
   
2. **Duplicate Insert Statement in `cars` Table:**
   - The script had repeated `INSERT INTO cars` statements at the end, which is redundant and removed.

3. **Use of Proper Data Types:**
   - Instead of using `VARCHAR(100)` for numerical values like `age`, `rent`, and `mileage`, consider using `INT` or `DECIMAL`.

4. **Adding Primary Keys:**
   - Ideally, `id` in each table should be set as `PRIMARY KEY` to avoid duplicate entries and maintain data integrity.

---

## Future Enhancements
- Implement `FOREIGN KEY` constraints between related tables, such as linking `carid` in `carbooking` to `id` in `cars`.
- Add **timestamp** columns to track record creation and updates.
- Normalize the database structure to minimize redundancy.
- Introduce **stored procedures** for efficient data retrieval.
- Implement **triggers** to validate data integrity.

---

## How to Use
1. **Database Setup:** Run the provided SQL script in MySQL, PostgreSQL, or any relational database management system.
2. **Data Entry:** Insert real-world data into the tables as needed.
3. **Querying Data:** Execute SQL queries to retrieve relevant booking, sales, and inquiry details.
4. **Modifications:** Extend the schema as per business needs.

---

## License
This project is open-source and available under the MIT License.

