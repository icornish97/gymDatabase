CREATE TABLE Employee
(employeeID number(4) NOT NULL,
eFirst varchar2(20),
eLast varchar2(20),
eStreet varchar2(15),
eCity varchar2(15),
eState varchar2(15),
eZipCode number(5),
ePhone number(10),
eHireDate date,
eFireDate date,
eStatus varchar2(8),
eType varchar2(25),
CONSTRAINT Employee_PK PRIMARY KEY(EmployeeID));

CREATE TABLE Customer
(CustomerID number(6) NOT NULL,
CFirst varchar2(20),
CLlast varchar2(20),
CStreetAddress varchar2(15),
CCity varchar2(15),
CState varchar2(15),
CZipCode number(5),
CHomePhone number(10),
CCellPhone number(10),
CAge number(3),
CDOB date,
CJoinDate date,
MembershipType varchar2(10),
CONSTRAINT Customer_PK PRIMARY KEY (CustomerID));

CREATE TABLE FitnessInstructor
(EmployeeID number(4) NOT NULL,
DateQualified date,
CONSTRAINT FitnessInstructor_PK PRIMARY KEY(EmployeeID),
CONSTRAINT FitnessInstructor_FK FOREIGN KEY(EmployeeID) REFERENCES Employee(EmployeeID));

CREATE TABLE Clerk
(EmployeeID number(4) NOT NULL,
HourlyRate number(5),
CONSTRAINT Clerk_PK PRIMARY KEY(EmployeeID),
CONSTRAINT Clerk_FK FOREIGN KEY(EmployeeID) REFERENCES Employee(EmployeeID));

CREATE TABLE AdministrativePersonnel
(EmployeeID number(4) NOT NULL,
Salary number(10),
CONSTRAINT AdministrativePersonnel_PK PRIMARY KEY(EmployeeID),
CONSTRAINT AdministrativePersonnel_FK FOREIGN KEY(EmployeeID) REFERENCES Employee(EmployeeID));

CREATE TABLE Owner
(EmployeeID number(4) NOT NULL,
Equity number(3),
CONSTRAINT Owner_PK PRIMARY KEY(EmployeeID),
CONSTRAINT Owner_FK FOREIGN KEY(EmployeeID) REFERENCES Employee(EmployeeID));

CREATE TABLE Manufacturer
(ManufacturerID number(8) NOT NULL,
Mfirst Varchar2(20),
Mlast Varchar2(20),
MStreetAddress Varchar2(15),
MCity Varchar2(15),
MState Varchar2(15),
MZipCode Number(5),
MPhoneNumber Number(10),
CONSTRAINT Manufacturer_PK PRIMARY KEY (ManufacturerID));

CREATE TABLE FitnessCourse
(FitnessCourseID number(8) NOT NULL,
CourseName varchar2(15),
CourseDescription varchar2(25),
CourseCategory varchar2(15),
CourseDuration varchar2(10),
CourseFee number (5),
CStartDate date,
CONSTRAINT FitnessCourse_PK PRIMARY KEY (FitnessCourseID));

CREATE TABLE Certificate
(EmployeeID number(4) NOT NULL,
FitnessCourseID number(8),
DateQualified date,
CONSTRAINT Certificate_PK PRIMARY KEY(EmployeeID, FitnessCourseID),
CONSTRAINT Certificate_FK FOREIGN KEY(EmployeeID) REFERENCES Employee(EmployeeID),
CONSTRAINT Certificate_FK2 FOREIGN KEY(FitnessCourseID) REFERENCES FitnessCourse(FitnessCourseID));

CREATE TABLE FitnessClass
(FitnessCourseID number(8) NOT NULL,
EmployeeID number(4) NOT NULL,
ClassName varchar2(10),
ClassDayOffer varchar2(15),
ClassDate date,
ClassDuration number(3),
CONSTRAINT FitnessClass_PK PRIMARY KEY (FitnessCourseID, EmployeeID),
CONSTRAINT FitnessClass_FK1 FOREIGN KEY (FitnessCourseID) REFERENCES FitnessCourse(FitnessCourseID),
CONSTRAINT FitnessClass_FK2 FOREIGN KEY (EmployeeID) REFERENCES Employee(EmployeeID));

CREATE TABLE Item 
(ItemID number(8) NOT NULL,
IMPrice number(7),
IRPrice number(7),
CONSTRAINT Item_PK PRIMARY KEY (ItemID));

CREATE TABLE Inventory
(InventoryID number(8) NOT NULL,
ItemID number(8) NOT NULL,
IRPoint number(4),
ItemQOH number(4),
CONSTRAINT Inventory_PK PRIMARY KEY (InventoryID),
CONSTRAINT Inventory_FK FOREIGN KEY (ItemID) REFERENCES Item(ItemID));

CREATE TABLE Shipment
(ShipmentID number(8) NOT NULL,
ItemID number(8) NOT NULL,
QReceived number(4),
DateReceived date,
CONSTRAINT Shipment_PK PRIMARY KEY (ShipmentID),
CONSTRAINT Foreign_FK FOREIGN KEY (ItemID) REFERENCES Item(ItemID));

CREATE TABLE Contractor
(ContractorID number(8) NOT NULL,
CFirst varchar2(20),
CLast varchar2(20),
CCompany varchar(20),
CPhone number(10),
CONSTRAINT Contractor_PK PRIMARY KEY (ContractorID));

CREATE TABLE Equipment
(EquipmentID number(8) NOT NULL,
EPurchaseDate date,
EMaintenanceDate date,
EquipmentType varchar2(15),
CONSTRAINT Equipment_PK PRIMARY KEY (EquipmentID));

CREATE TABLE Machine
(EquipmentID number(8) NOT NULL,
MachineType varchar2(20),
CONSTRAINT Machine_PK PRIMARY KEY (EquipmentID));

CREATE TABLE Inspection
(ContractorID number(8) NOT NULL,
EquipmentID number(8) NOT NULL,
LastInsDate date,
CONSTRAINT Inspection_PK PRIMARY KEY (ContractorID, EquipmentID),
CONSTRAINT Inspection_FK1 FOREIGN KEY (ContractorID) REFERENCES Contractor(ContractorID),
CONSTRAINT Inspection_FK2 FOREIGN KEY (EquipmentID) REFERENCES Machine(EquipmentID));

CREATE TABLE Weight
(EquipmentID number(8) NOT NULL,
WeightType varchar2(15),
WeightAmount number(3),
WeightBrand varchar2(15),
CONSTRAINT Weight_PK PRIMARY KEY (EquipmentID));

CREATE TABLE OrderLine
(ItemID number(8) NOT NULL,
OrderID number(8) NOT NULL,
Quantity number(4),
CONSTRAINT OrderLine_PK PRIMARY KEY (ItemID, OrderID),
CONSTRAINT OrderLine_FK1 FOREIGN KEY (ItemID) REFERENCES Item(ItemID),
CONSTRAINT OrderLIne_FK2 FOREIGN KEY (OrderID) REFERENCES Orders(OrderID));

CREATE TABLE Orders
(OrderID number(8) NOT NULL,
OrderDescription varchar(25),
OrderType varchar(10),
OrderDate date,
CONSTRAINT Order_PK PRIMARY KEY (OrderID));

CREATE TABLE Store
(OrderID number(8) NOT NULL,
ManufacturerID number(8),
CONSTRAINT Store_PK PRIMARY KEY (OrderID),
CONSTRAINT Store_FK FOREIGN KEY (ManufacturerID) REFERENCES Manufacturer(ManufacturerID));

CREATE TABLE Purchase
(OrderID number(8) NOT NULL,
PurchaseType varchar2(15),
DiscountRate decimal(2),
DirectorsDiscount decimal(2),
CONSTRAINT Purchase_PK PRIMARY KEY (OrderID));


CREATE TABLE Membership
(OrderID number(8) NOT NULL,
MFee number(3),
CONSTRAINT Membership_PK PRIMARY KEY (OrderID));

CREATE TABLE Merchandise
(OrderID number(8) NOT NULL,
ItemID number(8),
CONSTRAINT Merchandise_PK PRIMARY KEY (OrderID),
CONSTRAINT Merchandise_FK FOREIGN KEY (ItemID) REFERENCES Item(ItemID));

CREATE TABLE Facility
(FacilityRoomNo number(4) NOT NULL,
FacilityCapacity number(3),
CONSTRAINT Facility_PK PRIMARY KEY (FacilityRoomNo));

CREATE TABLE Location
(FacilityRoomNo number(4) NOT NULL,
EquipmentID number(8) NOT NULL,
CONSTRAINT Location_PK PRIMARY KEY (FacilityRoomNo, EquipmentID),
CONSTRAINT Location_FK1 FOREIGN KEY (FacilityRoomNo) REFERENCES Facility(FacilityRoomNo),
CONSTRAINT Location_FK2 FOREIGN KEY (EquipmentID) REFERENCES Equipment(EquipmentID));

CREATE TABLE Enrollment
(FitnessCourseID number(8) NOT NULL,
EmployeeID number(8) NOT NULL,
CustomerID number(6) NOT NULL,
CourseFee number(3) NOT NULL,
CONSTRAINT Enrollment_PK PRIMARY KEY (FitnessCourseID, EmployeeID, CustomerID),
CONSTRAINT Enrollment_FK1 FOREIGN KEY (FitnessCourseID) REFERENCES FitnessCourse(FitnessCourseID),
CONSTRAINT Enrollment_FK2 FOREIGN KEY (EmployeeID) REFERENCES Employee(EmployeeID),
CONSTRAINT Enrollment_FK3 FOREIGN KEY (CustomerID) REFERENCES Customer(CustomerID));

INSERT INTO Employee Values (5231, 'Daniel', 'Smith', '241 Main St', 'Ames', 'Iowa', 50010, 515431962, TO_DATE('02/11/2015', 'mm/dd/yyyy'), NULL, 'Active', 'Fitness Instructor');
INSERT INTO Employee Values (2843, 'Bobby', 'Martin', '631 North St', 'Ames', 'Iowa', 50014, 5154420162, TO_DATE('12/01/2014', 'mm/dd/yyyy'), TO_DATE('11/28/2017', 'mm/dd/yyyy'), 'Inactive', 'Clerk');
INSERT INTO Employee Values (3261, 'John', 'Smith', '918 Elm St', 'Ames', 'Iowa', 50014, 5153210192, TO_DATE('01/01/2007', 'mm/dd/yyyy'), NULL, 'Active', 'Owner');
INSERT INTO Employee Values (2345, 'Joan', 'Smith', '918 Elm St', 'Ames', 'Iowa', 50014, 5153210192, TO_DATE('01/01/2007', 'mm/dd/yyyy'), NULL, 'Active', 'Owner');
INSERT INTO Employee Values (2351, 'Ashley', 'White', '16 County Bvld', 'Boone', 'Iowa', 50036, 5156910189, TO_DATE('03/15/2010', 'mm/dd/yyyy'), NULL, 'Active', 'Administrative Personnel');
INSERT INTO Employee Values (9358, 'Marcus', 'Thomas', '421 River Dr', 'Story City', 'Iowa', 50248, 5159935389, TO_DATE('11/29/2017', 'mm/dd/yyyy'), NULL, 'Active', 'Clerk');
INSERT INTO Employee Values (6743, 'Mary', 'Matthews', '281 Clark St', 'Story City', 'Iowa', 50248, 5158755089, TO_DATE('03/17/2014', 'mm/dd/yyyy'), NULL, 'Active', 'Fitness Instructor');


INSERT INTO FitnessInstructor Values (5231, TO_DATE('01/10/2015', 'mm/dd/yyyy'));
INSERT INTO FitnessInstructor Values (6743, TO_DATE('02/13/2014', 'mm/dd/yyyy'));

INSERT INTO Clerk Values (2843, 10);
INSERT INTO Clerk Values (9358, 14);

INSERT INTO AdministrativePersonnel Values (2351, 50000);

INSERT INTO Owner Values (3261, 50);
INSERT INTO Owner Values (2345, 50);

INSERT INTO Manufacturer Values (29485172, 'Martin', 'Lewis', '415 Palm Dr', 'Anchorage', 'Alaska', 99501, 9072847148);
INSERT INTO Manufacturer Values (39582743, 'Lewis', 'Wayne', '732 Lucky St', 'Bozeman', 'Montana', 59715, 4068279148);
INSERT INTO Manufacturer Values (19248529, 'Martavis', 'Johnson', '86 Jersey St', 'Bozeman', 'Montana', 59715, 4067523910);
INSERT INTO Manufacturer Values (13952825, 'Jill', 'Mason', '682 Martin St', 'Omaha', 'Nebraska', 68007, 5313422910);
INSERT INTO Manufacturer Values (18259638, 'Damon', 'Williams', '613 Birch St', 'Omaha', 'Nebraska', 68007, 5313424322);

INSERT INTO Item Values (28596024, 10, 25);
INSERT INTO Item Values (12859242, 5, 12);
INSERT INTO Item Values (29483720, 7, 18);
INSERT INTO Item Values (83759273, 100, 250);
INSERT INTO Item Values (81237529, 75, 195);

INSERT INTO Inventory Values (92385738, 28596024, 20, 45);
INSERT INTO Inventory Values (93284375, 12859242, 50, 200);
INSERT INTO Inventory Values (29583721, 29483720, 35, 138);
INSERT INTO Inventory Values (83729504, 83759273, 5, 17);
INSERT INTO Inventory Values (72847291, 81237529, 8, 19);

INSERT INTO Shipment Values (18392852, 28596024, 32, TO_DATE('11/25/2017', 'mm/dd/yyyy'));
INSERT INTO Shipment Values (18273941, 12859242, 175, TO_DATE('11/25/2017', 'mm/dd/yyyy'));
INSERT INTO Shipment Values (74921923, 29483720, 110, TO_DATE('11/25/2017', 'mm/dd/yyyy'));
INSERT INTO Shipment Values (37251923, 83759273, 15, TO_DATE('11/25/2017', 'mm/dd/yyyy'));
INSERT INTO Shipment Values (18274257, 81237529, 25, TO_DATE('11/25/2017', 'mm/dd/yyyy'));

INSERT INTO Contractor Values (18392042, 'Mack', 'Parsons','Maintenance and More', 515682194);
INSERT INTO Contractor Values (12315123, 'Kelly', 'Smith','Repair World', 5156829401);
INSERT INTO Contractor Values (48294724, 'Dennis', 'Watson','First Rate Repair', 5151928377);
INSERT INTO Contractor Values (18252910, 'Ben', 'Peavey','Handyman for Hire', 5151391841);
INSERT INTO Contractor Values (92842315, 'Arnold', 'Clay','Maintenance For Less', 5159980732);

INSERT INTO Orders Values (38271923, 'FILLER', 'Purchase', TO_DATE('10/31/2017', 'mm/dd/yyyy'));
INSERT INTO Orders Values (72847193, 'FILLER', 'Purchase', TO_DATE('10/25/2017', 'mm/dd/yyyy'));
INSERT INTO Orders Values (83726419, 'FILLER', 'Purchase', TO_DATE('11/01/2017', 'mm/dd/yyyy'));
INSERT INTO Orders Values (56281023, 'FILLER', 'Store', TO_DATE('11/20/2017', 'mm/dd/yyyy'));
INSERT INTO Orders Values (87263910, 'FILLER', 'Store', TO_DATE('11/19/2017', 'mm/dd/yyyy'));

INSERT INTO OrderLine Values (28596024, 38271923, 2);
INSERT INTO OrderLine Values (12859242, 72847193, 5);
INSERT INTO OrderLine Values (29483720, 83726419, 1);
INSERT INTO OrderLine Values (83759273, 56281023, 15);
INSERT INTO OrderLine Values (81237529, 87263910, 25);

INSERT INTO Store Values (56281023, 13952825);
INSERT INTO Store Values (87263910, 18259638);

INSERT INTO Purchase Values (38271923,'Membership', 0, 0);
INSERT INTO Purchase Values (72847193,'Merchandise', .30, .10);
INSERT INTO Purchase Values (83726419,'Merchandise', .2, 0);

INSERT INTO Membership Values (38271923, 500);

INSERT INTO Merchandise Values (72847193, 12859242);
INSERT INTO Merchandise Values (83726419, 29483720);

INSERT INTO Facility Values (1123, 30);
INSERT INTO Facility Values (1124, 20);
INSERT INTO Facility Values (1125, 30);
INSERT INTO Facility Values (1126, 20);
INSERT INTO Facility Values (1127, 50);



INSERT INTO Customer Values (274812, 'Marty', 'Frank', '231 north st', 'Ames', 'Iowa', 50010, 5158291948, 5153720192, 17, TO_DATE('01/23/2000', 'mm/dd/yyyy'), TO_DATE('03/22/2015', 'mm/dd/yyyy'), 'Platinum');
INSERT INTO Customer Values (284914, 'Doug', 'Reiter', '233 frost st', 'Ames', 'Iowa', 50010, 5158341948, 5153723151, 20, TO_DATE('03/23/1997', 'mm/dd/yyyy'), TO_DATE('06/21/2015', 'mm/dd/yyyy'), 'Bronze');
INSERT INTO Customer Values (928314, 'George', 'Terry', '319 frost st', 'Ames', 'Iowa', 50010, 5158375632, 5153790131, 21, TO_DATE('06/02/1996', 'mm/dd/yyyy'), TO_DATE('08/23/2017', 'mm/dd/yyyy'), 'Silver');
INSERT INTO Customer Values (285161, 'Paul', 'Brown', '420 maple st', 'Ames', 'Iowa', 50010, 5158375912, 5153790201, 23, TO_DATE('09/21/1994', 'mm/dd/yyyy'), TO_DATE('12/24/2013', 'mm/dd/yyyy'), 'Gold');
INSERT INTO Customer Values (769248, 'Tyra', 'White', '469 market st', 'Ames', 'Iowa', 50010, 5158385212, 5153792801, 27, TO_DATE('09/21/1990', 'mm/dd/yyyy'), TO_DATE('12/24/2009', 'mm/dd/yyyy'), 'Platinum');

INSERT INTO FitnessCourse Values(87934516, 'Yoga', 'Yoga for Beginners', 'novice', '1 hour', 150, TO_DATE('01/15/2017','mm/dd/yyyy'));
INSERT INTO FitnessCourse Values(92845261, 'Yoga', 'Yoga for Experts', 'advanced', '1 hour', 200, TO_DATE('01/15/2017','mm/dd/yyyy'));
INSERT INTO FitnessCourse Values(28295382, 'Cardio', 'Group Run', 'Intermediate', '1 hour', 200, TO_DATE('01/15/2017','mm/dd/yyyy'));
INSERT INTO FitnessCourse Values(95862932, 'Pilates', 'Pilates for Beginners', 'novice', '1 hour', 150, TO_DATE('01/15/2017','mm/dd/yyyy'));
INSERT INTO FitnessCourse Values(67283521, 'Boxing', 'Boxing for Experts', 'advanced', '1 hour', 300, TO_DATE('01/15/2017','mm/dd/yyyy'));

INSERT INTO Enrollment Values (87934516, 5231, 274812, 150);
INSERT INTO Enrollment Values (92845261, 6743, 284914, 200);
INSERT INTO Enrollment Values (28295382, 5231, 928314, 300);
INSERT INTO Enrollment Values (95862932, 6743, 285161, 425);
INSERT INTO Enrollment Values (67283521, 5231, 769248, 100);

INSERT INTO Location Values (1123, 38271032);
INSERT INTO Location Values (1124, 18294276);
INSERT INTO Location Values (1125, 18920845);
INSERT INTO Location Values (1126, 56283928);
INSERT INTO Location Values (1127, 42098372);





INSERT INTO Inspection Values (18392042, 38271032, TO_DATE('03/23/2017', 'mm/dd/yyyy'));
INSERT INTO Inspection Values (12315123, 18294276, TO_DATE('07/19/2017', 'mm/dd/yyyy'));
INSERT INTO Inspection Values (48294724, 18920845, TO_DATE('04/11/2017', 'mm/dd/yyyy'));
INSERT INTO Inspection Values (18252910, 56283928, TO_DATE('11/19/2017', 'mm/dd/yyyy'));
INSERT INTO Inspection Values (92842315, 42098372, TO_DATE('11/08/2017', 'mm/dd/yyyy'));






INSERT INTO Equipment values(38271032, TO_DATE('01-01-2017','mm-dd-yyyy'), TO_DATE('1-15-2017','mm-dd-yyyy'), 'Machine');

INSERT INTO Equipment values(18294276, TO_DATE('01-02-2017','mm-dd-yyyy'), TO_DATE('1-15-2017','mm-dd-yyyy'), 'Machine');

INSERT INTO Equipment values(18920845, TO_DATE('01-04-2017','mm-dd-yyyy'), TO_DATE('1-15-2017','mm-dd-yyyy'), 'Machine');

INSERT INTO Equipment values(56283928, TO_DATE('01-05-2017','mm-dd-yyyy'), TO_DATE('1-15-2017','mm-dd-yyyy'), 'Weight');

INSERT INTO Equipment values(42098372, TO_DATE('01-06-2017','mm-dd-yyyy'), TO_DATE('1-15-2017','mm-dd-yyyy'), 'Weight');


INSERT INTO Certificate Values(5231, 87934516, TO_DATE('05/18/2016','mm/dd/yyyy'));
INSERT INTO Certificate Values(5231, 92845261, TO_DATE('05/18/2016','mm/dd/yyyy'));
INSERT INTO Certificate Values(6743, 28295382, TO_DATE('11/06/2016','mm/dd/yyyy'));
INSERT INTO Certificate Values(5231, 95862932, TO_DATE('06/24/2016','mm/dd/yyyy'));
INSERT INTO Certificate Values(6743, 67283521, TO_DATE('09/15/2016','mm/dd/yyyy'));


INSERT INTO Weight Values (56283928, 'Kettlebell', 50, 'Kings');
INSERT INTO Weight Values (42098372, 'Dumbbell', 25, 'Marcy');

INSERT INTO Machine values(38271032, 'Treadmill');
INSERT INTO Machine values(18294276, 'Exercise Bike');
INSERT INTO Machine values(18920845, 'Elliptical');





INSERT INTO FitnessClass Values (87934516, 5231, 'Yoga', 'M', TO_DATE('01/01/2018'), 1);
INSERT INTO FitnessClass Values (87934516, 6743, 'Yoga', 'M/W/F', TO_DATE('01/01/2018'), 1 );
INSERT INTO FitnessClass Values (28295382, 6743, 'Cardio', 'Th/F', TO_DATE('01/04/2018'), 1.2);
INSERT INTO FitnessClass Values(28295382, 5231, 'Cardio', 'M', TO_DATE('01/08/2018'), 1);
INSERT INTO FitnessClass Values(67283521, 6743, 'Boxing', 'M', TO_DATE('01/18/2018'), 1);
