 Step 1: Create Tables
CREATE TABLE Customers (
    CustomerID INT PRIMARY KEY,
    Name TEXT,
    City TEXT
);

CREATE TABLE Orders (
    OrderID INT PRIMARY KEY,
    CustomerID INT,
    Product TEXT,
    FOREIGN KEY (CustomerID) REFERENCES Customers(CustomerID)
);

Step 2: Insert Sample Data
INSERT INTO Customers (CustomerID, Name, City) VALUES
(1, 'Alice', 'New York'),
(2, 'Bob', 'Los Angeles'),
(3, 'Charlie', 'Chicago'),
(4, 'Diana', 'Houston');

INSERT INTO Orders (OrderID, CustomerID, Product) VALUES
(101, 1, 'Laptop'),
(102, 2, 'Phone'),
(103, 1, 'Tablet'),
(104, 5, 'Camera');  

Step 3: INNER JOIN
SELECT 'INNER JOIN' AS JoinType, Customers.Name, Orders.Product
FROM Customers
INNER JOIN Orders ON Customers.CustomerID = Orders.CustomerID;

Step 4: LEFT JOIN
SELECT 'LEFT JOIN' AS JoinType, Customers.Name, Orders.Product
FROM Customers
LEFT JOIN Orders ON Customers.CustomerID = Orders.CustomerID;

 Step 5: RIGHT JOIN (MySQL/PostgreSQL only)
 SELECT 'RIGHT JOIN' AS JoinType, Customers.Name, Orders.Product
 FROM Customers
 RIGHT JOIN Orders ON Customers.CustomerID = Orders.CustomerID;

 Step 6: FULL OUTER JOIN (Only works in PostgreSQL / some DBs)
 SQLite does NOT support FULL OUTER JOIN, simulate using UNION

SELECT 'FULL JOIN SIMULATION' AS JoinType, Customers.Name, Orders.Product
FROM Customers
LEFT JOIN Orders ON Customers.CustomerID = Orders.CustomerID

UNION
SELECT 'FULL JOIN SIMULATION' AS JoinType, Customers.Name, Orders.Product
FROM Orders
LEFT JOIN Customers ON Customers.CustomerID = Orders.CustomerID;
