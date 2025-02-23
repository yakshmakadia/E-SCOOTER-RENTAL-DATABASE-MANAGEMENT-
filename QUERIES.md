# SQL Queries

## 1. Create Tables
```sql
CREATE TABLE Users (
    user_id INT AUTO_INCREMENT PRIMARY KEY,
    name VARCHAR(100),
    email VARCHAR(100) UNIQUE,
    phone VARCHAR(15),
    password_hash VARCHAR(255)
);

CREATE TABLE Scooters (
    scooter_id INT AUTO_INCREMENT PRIMARY KEY,
    model VARCHAR(50),
    status ENUM('available', 'rented', 'maintenance'),
    location VARCHAR(100)
);

CREATE TABLE Rentals (
    rental_id INT AUTO_INCREMENT PRIMARY KEY,
    user_id INT,
    scooter_id INT,
    start_time DATETIME,
    end_time DATETIME,
    cost DECIMAL(10,2),
    FOREIGN KEY (user_id) REFERENCES Users(user_id),
    FOREIGN KEY (scooter_id) REFERENCES Scooters(scooter_id)
);
```

## 2. Insert Sample Data
```sql
INSERT INTO Users (name, email, phone, password_hash) VALUES
('John Doe', 'john@example.com', '1234567890', 'hashedpassword1'),
('Jane Smith', 'jane@example.com', '0987654321', 'hashedpassword2');

INSERT INTO Scooters (model, status, location) VALUES
('Xiaomi Mi', 'available', 'Station A'),
('Segway Ninebot', 'available', 'Station B');
```

## 3. Retrieve Available Scooters
```sql
SELECT * FROM Scooters WHERE status = 'available';
```

## 4. Rent a Scooter
```sql
UPDATE Scooters SET status = 'rented' WHERE scooter_id = 1;
INSERT INTO Rentals (user_id, scooter_id, start_time) VALUES (1, 1, NOW());
```

## 5. Return a Scooter
```sql
UPDATE Scooters SET status = 'available' WHERE scooter_id = 1;
UPDATE Rentals SET end_time = NOW(), cost = 5.00 WHERE rental_id = 1;
```

