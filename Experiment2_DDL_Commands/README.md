# Experiment 2: DDL Commands

## AIM
To study and implement DDL commands and different types of constraints.

## THEORY

### 1. CREATE
Used to create a new relation (table).

**Syntax:**
```sql
CREATE TABLE (
  field_1 data_type(size),
  field_2 data_type(size),
  ...
);
```
### 2. ALTER
Used to add, modify, drop, or rename fields in an existing relation.
(a) ADD
```sql
ALTER TABLE std ADD (Address CHAR(10));
```
(b) MODIFY
```sql
ALTER TABLE relation_name MODIFY (field_1 new_data_type(size));
```
(c) DROP
```sql
ALTER TABLE relation_name DROP COLUMN field_name;
```
(d) RENAME
```sql
ALTER TABLE relation_name RENAME COLUMN old_field_name TO new_field_name;
```
### 3. DROP TABLE
Used to permanently delete the structure and data of a table.
```sql
DROP TABLE relation_name;
```
### 4. RENAME
Used to rename an existing database object.
```sql
RENAME TABLE old_relation_name TO new_relation_name;
```
### CONSTRAINTS
Constraints are used to specify rules for the data in a table. If there is any violation between the constraint and the data action, the action is aborted by the constraint. It can be specified when the table is created (using CREATE TABLE) or after it is created (using ALTER TABLE).
### 1. NOT NULL
When a column is defined as NOT NULL, it becomes mandatory to enter a value in that column.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size) NOT NULL
);
```
### 2. UNIQUE
Ensures that values in a column are unique.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size) UNIQUE
);
```
### 3. CHECK
Specifies a condition that each row must satisfy.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size) CHECK (logical_expression)
);
```
### 4. PRIMARY KEY
Used to uniquely identify each record in a table.
Properties:
Must contain unique values.
Cannot be null.
Should contain minimal fields.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size) PRIMARY KEY
);
```
### 5. FOREIGN KEY
Used to reference the primary key of another table.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size),
  FOREIGN KEY (column_name) REFERENCES other_table(column)
);
```
### 6. DEFAULT
Used to insert a default value into a column if no value is specified.

Syntax:
```sql
CREATE TABLE Table_Name (
  col_name1 data_type,
  col_name2 data_type,
  col_name3 data_type DEFAULT 'default_value'
);
```

**Question 1**
<img width="1573" height="422" alt="image" src="https://github.com/user-attachments/assets/a93e14c7-2717-4f4f-9455-a4f6bfc272d7" />


```
create table Products(
ProductID INTEGER primary key,
ProductName TEXT unique not NULL,
Price REAL check(Price>0),
StockQuantity INTEGER check(StockQuantity>=0)
);
```

**Output:**

<img width="1873" height="201" alt="image" src="https://github.com/user-attachments/assets/2df54cdc-a535-4de2-913d-6fa484a53580" />


**Question 2**
<img width="946" height="386" alt="image" src="https://github.com/user-attachments/assets/c81eef29-8aa1-4049-9879-3c8f7c6058b3" />


```
insert into Customers (CustomerID, Name, Address, Email)
select CustomerID, Name, Address, Email from Old_customers;
```

**Output:**
<img width="1633" height="261" alt="image" src="https://github.com/user-attachments/assets/2669f8f2-e096-4d24-93fb-6a00899fdfe0" />


**Question 3**
<img width="1048" height="403" alt="image" src="https://github.com/user-attachments/assets/d9179080-6124-4150-ab35-9cac1df82097" />


```
insert into Employee (EmployeeID, Name, Position) values (4,'Emily White','Analyst')
```

**Output:**
<img width="1143" height="308" alt="image" src="https://github.com/user-attachments/assets/1561ccdd-ea5e-4344-8264-0934756d5298" />


**Question 4**
<img width="1048" height="364" alt="image" src="https://github.com/user-attachments/assets/ddf05e47-0340-425f-9844-a8725d9a4f6c" />


```
create table Departments(
DepartmentID INTEGER,
DepartmentName TEXT
);
```

**Output:**
<img width="1707" height="306" alt="image" src="https://github.com/user-attachments/assets/7e5f60f5-9e71-4b43-a6d1-857f5c069cdb" />


**Question 5**
<img width="1433" height="338" alt="image" src="https://github.com/user-attachments/assets/1a5e19c2-be4a-48cb-ad2f-c2c04cbc460f" />


```
create table Orders(
OrderID INTEGER primary key,
OrderDate DATE not NULL,
CustomerID INTEGER,
foreign key (CustomerID) references Customers(CustomerID)
);
```

**Output:**
<img width="1879" height="239" alt="image" src="https://github.com/user-attachments/assets/58306034-ce0f-4126-9a26-831c794745ae" />


**Question 6**

<img width="736" height="353" alt="image" src="https://github.com/user-attachments/assets/f7d99f2e-4809-4834-b8e5-e99bb10c5b2b" />


```
create table Products(
ProductID primary key,
ProductName NOT NULL,
Price real check(Price>0),
Stock integer check(Stock>=0)
);
```

**Output:**
<img width="1360" height="244" alt="image" src="https://github.com/user-attachments/assets/8ed63823-7b3d-4762-8f27-4e04bc3c223f" />


**Question 7**
<img width="1023" height="586" alt="image" src="https://github.com/user-attachments/assets/b06ecb2c-b65b-4ed9-9a1b-541e4a8590fe" />


```
alter table Student_details
add Mobilenumber number;
```

**Output:**
<img width="1711" height="326" alt="image" src="https://github.com/user-attachments/assets/dde3b25e-7e3e-4400-b7d4-b51d1f987de2" />


**Question 8**
<img width="1016" height="455" alt="image" src="https://github.com/user-attachments/assets/6695db1b-6df0-4d15-a199-7c4c6f0be8c2" />



```
create table item(
item_id TEXT primary key,
item_desc TEXT,
rate INTEGER,
icom_id TEXT(4),
foreign key(icom_id) references company(com_id) on update cascade on delete cascade 
);
```

**Output:**
<img width="1517" height="306" alt="image" src="https://github.com/user-attachments/assets/99925ef4-749b-4978-ae31-300d7e1803c7" />



**Question 9**
<img width="1698" height="456" alt="image" src="https://github.com/user-attachments/assets/8780b3a0-0ff0-4002-8301-b92306f66f33" />


```
insert into Customers(CustomerId,Name,Address) values(306,'Diana Prince','Themyscira');
insert into Customers(CustomerId,Name,Address,City,ZipCode) values(307,'Bruce Wayne','Wayne Manor','Gotham',10007);
insert into Customers(CustomerId,Name,Address,ZipCode) values(308,'Peter Parker','Queens',11375);
```

**Output:**
<img width="1455" height="250" alt="image" src="https://github.com/user-attachments/assets/1dc25de0-cd25-4326-8cde-038f6beb3a75" />


**Question 10**
<img width="1010" height="584" alt="image" src="https://github.com/user-attachments/assets/92a279a0-e146-4f4c-8922-244d94ee6833" />


```
alter table Student_details
add mobilenumber number;
```

**Output:**
<img width="1716" height="318" alt="image" src="https://github.com/user-attachments/assets/bd220281-1578-48d7-8fec-faf248643805" />

## Score:
<img width="1402" height="247" alt="image" src="https://github.com/user-attachments/assets/59c373b0-d0f0-4b84-92f7-ae26bd7b3f77" />


## RESULT
Thus, the SQL queries to implement different types of constraints and DDL commands have been executed successfully.
