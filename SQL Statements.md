# Create Database and Tables
```
Create Database DecorworxProject2;  
go  
```

```
Create TABLE Customer(  
   CustomerID INT IDENTITY(1,1) PRIMARY KEY,  
   CustomerName VARCHAR(255) NOT Null,  
   ContactPhysicalAddress VARCHAR(255) NOT Null,  
   ContactMailingAddress VARChar(255) NOT NULL,  
   ContactPhone NVARCHAR(12) Not Null Unique,   
   PhoneTextAvailable BIT Not Null,  
   ContactEmail VARCHAR(50) Not Null,   
);
```

```
Create Table Orders(  
|       OrderID INT IDENTITY(1,1) PRIMARY KEY,  
|       CustomerID INT FOREIGN KEY REFERENCES Customer(CustomerID),  
|       EstimatedCost INT,  
|       ShippingAddress VARCHAR(255) Not Null,  
|       OrderSize VARCHAR(10) Not Null,  
|       Install BIT Not Null,  
);  
```

```
Create Table Items(  
|       ItemID INT IDENTITY(1,1) Primary Key,  
|       ItemName VarChar(100) Not Null,  
);

Create Table OrderItems(  
|       OrderID INT FOREIGN KEY REFERENCES Orders(OrderID),  
|       ItemID INT FOREIGN Key REFERENCES Items(ItemID),  
);

Create Table Processes(  
|       ProcessID INT IDENTITY(1,1) PRIMARY KEY,   
|       ProcessName VARCHAR(50) Not Null,  
|       ProcessMachine VARCHAR(50) Not Null,  
|       Department VARCHAR(50) Not Null,   
);

Create Table Employees(
|       EmployeeID INT IDENTITY(1,1) PRIMARY KEY,  
|       EmployeeName VARCHAR(40) Not Null,  
|       Experience VARCHAR(10),  
);

Create TABLE ItemProcesses (
 |      ItemID INT FOREIGN KEY REFERENCES Items(ItemID),  
|       ProcessID INT FOREIGN KEY REFERENCES Processes(ProcessID),  
|       EmployeeID int FOREIGN KEY REFERENCES Employees(EmployeeID),  
|       EmployeePercentCompleted int,  
|       Specifications VARCHAR(255),  
);

Create TABLE Supplies(
|       SupplyID INT IDENTITY(1,1) PRIMARY Key,  
|       SupplyName VARCHAR(100) NOt Null,  
|       QuantityInStock int,  
);

Create Table ItemOrderSupplies (  
 |      ItemID INT FOREIGN KEY REFERENCES Items(ItemID),  
|       SupplyID INT FOREIGN KEY REFERENCES Supplies(SupplyID),  
);

Create Table Suppliers(  
|       SupplierID INT IDENTITY(1,1) PRIMARY KEY,  
|       SupplierName VARCHAR(50) Not NULL,  
|       ContactAddress VarChar(100) NOT NULL,    
|       ContactEmail VarChar(50) Not Null,   
);

Create Table SupplierSupplies(  
|       SupplyID INT FOREIGN KEY REFERENCES Supplies(SupplyID),  
|       SupplierID INT FOREIGN KEY REFERENCES Suppliers(SupplierID),  
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

## Supplies
INSERT Into Supplies (SupplyName, QuantityInStock) VALUES   
('Acrylic',10),  
('Alder Veneer', 50),  
('Gator Foam', 10),  
('MDF', 30),  
('Sintra (FoamPVC)', 20),  
('Wrisco- Brushed Silver 4x8',6),  
('ACM (Aluminum Composite Material)', 75),  
('Aluminum', 40),  
('94 CA Spray Adhesive', 1005),  
('Acorn Nuts-Black', 547),  
('Acoustical-Lag',364)  

![Screenshot_20221202_085846](https://user-images.githubusercontent.com/40216815/205421720-9c227ec3-7df1-4566-baad-71794c1f2759.png)  

Select * From Supplies;
 
![Screenshot_20221202_085857](https://user-images.githubusercontent.com/40216815/205421728-b2d7d2d8-4666-4ce6-989b-d38b525ecd2d.png)

## Employees
INSERT Into Employees (EmployeeName, Experience) VALUES 
('Melissa Shannon',10),
('Terrance Farnsworth',1),
('Julie Ellis',6),
('Patrick Shannon',10),
('Tenia Wallace',7),
('Jaxon Haderlie',9),
('Ciara Fails',3),
('Steve Ellis',5),
('Jeff Dansie',10),
('Lalena Taylor',4)

![Screenshot_20221202_092102](https://user-images.githubusercontent.com/40216815/205422615-bed52fff-6fe3-447a-aac3-216523beec6f.png)

Select * From Employees;
![Screenshot_20221202_092115](https://user-images.githubusercontent.com/40216815/205422630-fe6d6355-3f1e-47b4-8cfc-6cb5a25cb740.png)

## Processess
INSERT Into Processes (ProcessName, ProcessMachine, Department) VALUES 
('Printing', '180 Color Jet Extreme', 'Manufacturing'),
('Routing', 'Multi Cam 3000', 'Manufacturing'),
('Routing', 'Jet Cam Router', 'Manufacturing'),
('Painting', 'Easy Flow Sprayer', 'Manufacturing'),
('Assembly', 'NA', 'Manufacturing'),
('Install', 'NA', 'Install')
![Screenshot_20221202_093602](https://user-images.githubusercontent.com/40216815/205423216-a05e5f5a-4dcd-4dca-9c95-aef20d36eb04.png)  

select * From Processes;

![Screenshot_20221202_093608](https://user-images.githubusercontent.com/40216815/205423219-5e4d7a23-815d-4e2f-b557-36c991d031bc.png)

## Items
INSERT Into Items (ItemName) VALUES 
('box'),
('letters'),
('poster'),
('sign'),
('label'),
('backing'),
('light box'),
('frame'),
('banner'),
('photo print'),
('icon'),
('menu'),
('check boxes'),
('poles'),
('trellis')  
go
![Screenshot_20221202_102803](https://user-images.githubusercontent.com/40216815/205425704-d9a7a30c-c65d-4b8b-baef-d4e95d575ce4.png)


select * From Items;
![Screenshot_20221202_102811](https://user-images.githubusercontent.com/40216815/205425728-96529761-6df0-47a8-a4ae-510c13099ecf.png)

## Customer
INSERT Into Customer (CustomerName, ContactPhysicalAddress,ContactMailingAddress, ContactPhone, PhoneTextAvailable, ContactEmail) VALUES 
('George Baines', '350 E 100 N, Cedar City,', '350 E 100 N, Cedar City,', '435-999-5555', 1, 'georgebaines@gmail.com')
('Nataly Townsend ', '300 Forrest Street, Enoch', 'PO Box 334', '435-111-8877', 0, 'natallytownsend@gmail.com'),
('Walgreens', '4435 E 200 N, Houston, TX', '4435 E 200 N, Houston, TX', '112-335-8954',0 , 'greg@walgreens.org'),
go

![Screenshot_20221202_105456](https://user-images.githubusercontent.com/40216815/205426729-40f78060-428a-4f25-b768-49274ec7a06e.png)  

select * From Customer;

![Screenshot_20221202_105600](https://user-images.githubusercontent.com/40216815/205426784-b73e48be-13f3-4d66-86bc-131dec2d6676.png)

## Orders
INSERT Into Orders (CustomerID, EstimatedCost, ShippingAddress, OrderSize, Install) VALUES 
(1,5438, 'Elm Street, Houston, TX', 20, 1),
(2,150 , '300 Forrest Street, Enoch',3 ,0 ),
(3,20000 , '4435 E 200 N, Houston, TX',20 ,1),
(3,18250, '4435 E 200 N, Houston, TX',4 ,1)
go
![Screenshot_20221202_110533](https://user-images.githubusercontent.com/40216815/205427187-76e306ec-210f-4a7c-b465-bb13dac71889.png)


select * From Orders;
![Screenshot_20221202_110543](https://user-images.githubusercontent.com/40216815/205427188-b11b3bb2-aec0-445c-8c48-ec1675601b2c.png)

## OrderItems
INSERT Into OrderItems (OrderID, ItemID) VALUES 
(1,1),
(1,4),
(1,14),
(1,15),
(2,4),
(3,1),
(3,11),
(3,13),
(3,2),
(3,1),
(3,10),
(4,3),
(4,9)
go

![Screenshot_20221202_111239](https://user-images.githubusercontent.com/40216815/205427512-26b51840-feac-472e-9e8d-fd449b8e0372.png)


select * From OrderItems;

![Screenshot_20221202_111245](https://user-images.githubusercontent.com/40216815/205427515-5c6a7390-ac8f-43ed-97a0-438eaab6d5e5.png)

## ItemProcesses
INSERT Into ItemProcesses (ItemID, ProcessID, EmployeeID, EmployeePercentCompleted, Specifications) VALUES 
(2,1,4,20,'Black and White'),
(2,2,2,30,'Route'),
(2,5,9,70,'assemble'),
(1,4,4,10,'paint')
go
![Screenshot_20221202_112140](https://user-images.githubusercontent.com/40216815/205427835-cd271b8f-0ad7-401a-9737-734c740f316e.png)


select * From ItemProcesses;
![Screenshot_20221202_112146](https://user-images.githubusercontent.com/40216815/205427839-fc8356e6-cd3a-46aa-a493-291e732bc791.png)

# User Queries
select SupplyName, QuantityInStock From Supplies;
![Screenshot_20221202_112548](https://user-images.githubusercontent.com/40216815/205427951-35ee1f6b-8cd5-4ca8-aee7-ba324ba4e79b.png)


select SupplierName
From Suppliers
Where ContactAddress LIKE'%TX%';
![Screenshot_20221202_113840](https://user-images.githubusercontent.com/40216815/205428310-ef56d1f8-5614-4655-8853-adb3a93619f6.png)

![Screenshot_20221202_113845](https://user-images.githubusercontent.com/40216815/205428313-a190fd80-a64f-4a78-a45c-0c84673e5bba.png)

# Views



# Procedures
 
# Triggers

# User Groups and Roles
Create LOGIN Administrator WITH Password ='DatabaseDefensive.' 
Create LOGIN Sales With PASSWORD ='Salesrep4456'

