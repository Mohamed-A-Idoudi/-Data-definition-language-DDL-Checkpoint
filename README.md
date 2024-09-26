# -Data-definition-language-DDL-Checkpoint:
-- Create the CUSTOMER table
CREATE TABLE CUSTOMER (
    CustomerID NUMBER PRIMARY KEY,
    FirstName VARCHAR2(50),
    LastName VARCHAR2(50),
    Address VARCHAR2(100),
    Phone VARCHAR2(20),
    Email VARCHAR2(50)
);

-- Create the PRODUCT table
CREATE TABLE PRODUCT (
    ProductID NUMBER PRIMARY KEY,
    ProductName VARCHAR2(50),
    Price NUMBER,
    Stock NUMBER
);

-- Create the ORDERS table
CREATE TABLE ORDERS (
    OrderID NUMBER PRIMARY KEY,
    CustomerID NUMBER,
    OrderDate DATE DEFAULT SYSDATE, -- New column with default value
    CONSTRAINT fk_customer
      FOREIGN KEY (CustomerID)
      REFERENCES CUSTOMER(CustomerID)
);

-- Create the ORDER_LINE table
CREATE TABLE ORDER_LINE (
    OrderLineID NUMBER PRIMARY KEY,
    OrderID NUMBER,
    ProductID NUMBER,
    Quantity NUMBER,
    CONSTRAINT fk_order
      FOREIGN KEY (OrderID)
      REFERENCES ORDERS(OrderID),
    CONSTRAINT fk_product
      FOREIGN KEY (ProductID)
      REFERENCES PRODUCT(ProductID)
);

-- Add a new Category column to the PRODUCT table
ALTER TABLE PRODUCT
ADD Category VARCHAR2(20);
