# Create Database and Tables
Create Database DecorworxProject2;
go 
Create TABLE Customer(
    CustomerID INT IDENTITY(1,1) PRIMARY KEY,
    CustomerName VARCHAR(255) NOT Null,
    ContactPhysicalAddress VARCHAR(255) NOT Null,
    ContactMailingAddress VARChar(255) NOT NULL,
    ContactPhone NVARCHAR(12) Not Null Unique, 
    PhoneTextAvailable BIT Not Null,
    ContactEmail VARCHAR(50) Not Null, 
);

Create Table Orders(
    OrderID INT IDENTITY(1,1) PRIMARY KEY,
    CustomerID INT FOREIGN KEY REFERENCES Customer(CustomerID),
    EstimatedCost INT,
    ShippingAddress VARCHAR(255) Not Null,
    OrderSize VARCHAR(10) Not Null,
    Install BIT Not Null,
);

Create Table Items(
    ItemID INT IDENTITY(1,1) Primary Key,
    ItemName VarChar(100) Not Null,
);

Create Table OrderItems(
    OrderID INT FOREIGN KEY REFERENCES Orders(OrderID),
    ItemID INT FOREIGN Key REFERENCES Items(ItemID),
);

Create Table Processes(
    ProcessID INT IDENTITY(1,1) PRIMARY KEY, 
    ProcessName VARCHAR(50) Not Null,
    ProcessMachine VARCHAR(50) Not Null,
    Department VARCHAR(50) Not Null, 
);

Create Table Employees(
    EmployeeID INT IDENTITY(1,1) PRIMARY KEY,
    EmployeeName VARCHAR(40) Not Null,
    Experience VARCHAR(10),
);

Create TABLE ItemProcesses (
    ItemID INT FOREIGN KEY REFERENCES Items(ItemID),
    ProcessID INT FOREIGN KEY REFERENCES Processes(ProcessID),
    EmployeeID int FOREIGN KEY REFERENCES Employees(EmployeeID),
    EmployeePercentCompleted int,
    Specifications VARCHAR(255),
);

Create TABLE Supplies(
    SupplyID INT IDENTITY(1,1) PRIMARY Key,
    SupplyName VARCHAR(100) NOt Null,
    QuantityInStock int,
);

Create Table ItemOrderSupplies (
    ItemID INT FOREIGN KEY REFERENCES Items(ItemID),
    SupplyID INT FOREIGN KEY REFERENCES Supplies(SupplyID),
);

Create Table Suppliers(
    SupplierID INT IDENTITY(1,1) PRIMARY KEY,
    SupplierName VARCHAR(50) Not NULL,
    ContactAddress VarChar(100) NOT NULL,
    ContactEmail VarChar(50) Not Null, 
);

Create Table SupplierSupplies(
    SupplyID INT FOREIGN KEY REFERENCES Supplies(SupplyID),
    SupplierID INT FOREIGN KEY REFERENCES Suppliers(SupplierID),
);


# Insert Statements
## Suppliers
INSERT Into Suppliers (SupplierName, ContactAddress, ContactEmail) VALUES    
('Home Depot', '1518 S Providence Center Dr, Cedar City, UT 84720', 'Gerard@homedepot.com'),   
('Small Town Suppliers', '15 E 100 S, Kansas City, KS 66012', 'AmeliaBedila@yahoomail.com'),  
('This and That', 'PO Box 3345, Soda Springs, ID 83276', 'happygolucky@gmail.com'),  
('Storefront Suppliers',' 1436 N 300 W, New York, NY 10001','stevensharp@storefrontsuppliers.org'),  
('Silly Strings Suppliers','PO Box 1123, New York, NY 10005','sillystringsrep@sillystringsuppliers.com'),  
('Region Supplier','13, Jalan SS 26/8, Taman Mayang Jaya, 47301 Petaling Jaya, Selangor, Malaysia','chen@regionalsuppliers.org'),  
('Serra Forest Products','316 E 1400 S Suite B1, St. George, UT 84790','JamesMontrose@sierraforestproducts.com'),  
('HP','10300 Energy Dr, Spring, TX 77389','carsonford@hpinc.com'),  
('Hartlauer',' 3900 W Dewey Dr, Las Vegas, NV 89118','donjuan@hartlauer.com'),  
('Multicam','DFW Airport, 1025 W Royal Ln, Dallas, TX 75261','juanrodriges@multicam.com')  

select * From Suppliers;
![Screenshot_20221202_083831](https://user-images.githubusercontent.com/40216815/205420921-d3d0415a-6be0-4450-98e3-044071e5fc59.png)

 

# User Queries

# Views

# Procedures
 
# Triggers

# User Groups and Roles
