-- Create Database
CREATE DATABASE Escooter_dbms;
USE Escooter_dbms;

-- Create Company Table
CREATE TABLE Company (
    registration_id INT PRIMARY KEY, 
    name VARCHAR(255) NOT NULL, 
    no_of_vehicles_rented INT NOT NULL, 
    UNIQUE (name)
);

-- Create City Table
CREATE TABLE City (
    name VARCHAR(255) PRIMARY KEY, 
    total_vehicle INT NOT NULL
);

-- Create RentingStation Table
CREATE TABLE RentingStation (
    station_id INT PRIMARY KEY, 
    address VARCHAR(255) NOT NULL, 
    avail_scooter INT NOT NULL, 
    phone_no BIGINT(10) NOT NULL, 
    FOREIGN KEY (station_id) REFERENCES Company(registration_id)
);

-- Create User Table
CREATE TABLE User (
    user_id INT PRIMARY KEY, 
    phone_no BIGINT(10) NOT NULL, 
    name CHAR(20) NOT NULL, 
    age INT, 
    DOB DATE, 
    UNIQUE (phone_no)
);

-- Create Scooter Table
CREATE TABLE Scooter (
    scooter_id VARCHAR(255) PRIMARY KEY, 
    price INT NOT NULL, 
    location VARCHAR(255) NOT NULL, 
    service_due DATE, 
    FOREIGN KEY (location) REFERENCES City(name)
);

-- Create Ledger Table
CREATE TABLE Ledger (
    transaction_id INT PRIMARY KEY, 
    rented_at DATETIME NOT NULL, 
    returned_at DATETIME, 
    scooter_id VARCHAR(255), 
    FOREIGN KEY (scooter_id) REFERENCES Scooter(scooter_id), 
    FOREIGN KEY (transaction_id) REFERENCES User(user_id)
);
