# Experiment 5: Subqueries and Views

## AIM
To study and implement subqueries and views.

## THEORY

### Subqueries
A subquery is a query inside another SQL query and is embedded in:
- WHERE clause
- HAVING clause
- FROM clause

**Types:**
- **Single-row subquery**:
  Sub queries can also return more than one value. Such results should be made use along with the operators in and any.
- **Multiple-row subquery**:
  Here more than one subquery is used. These multiple sub queries are combined by means of ‘and’ & ‘or’ keywords.
- **Correlated subquery**:
  A subquery is evaluated once for the entire parent statement whereas a correlated Sub query is evaluated once per row processed by the parent statement.

**Example:**
```sql
SELECT * FROM employees
WHERE salary > (SELECT AVG(salary) FROM employees);
```
### Views
A view is a virtual table based on the result of an SQL SELECT query.
**Create View:**
```sql
CREATE VIEW view_name AS
SELECT column1, column2 FROM table_name WHERE condition;
```
**Drop View:**
```sql
DROP VIEW view_name;
```

**Question 1**
<img width="1229" height="570" alt="image" src="https://github.com/user-attachments/assets/3c7e1012-6261-4cb0-bbf0-50727704fdc1" />


```sql
select * from orders
where salesman_id in(
select salesman_id from orders
where customer_id=3007);
```

**Output:**

<img width="1235" height="422" alt="image" src="https://github.com/user-attachments/assets/9a52f9af-8858-40f6-bdda-e2c085d76a5a" />


**Question 2**
<img width="1184" height="824" alt="image" src="https://github.com/user-attachments/assets/dc2cc0d1-de08-4187-aa34-ecdbfa7eafd8" />


```sql
select * from ORDERS
where salesman_id in(
select salesman_id from SALESMAN
where city='New York');
```

**Output:**

<img width="1219" height="460" alt="image" src="https://github.com/user-attachments/assets/94e7e425-dc54-444e-96a8-41261a9fa23b" />


**Question 3**
<img width="983" height="633" alt="image" src="https://github.com/user-attachments/assets/42475d52-da58-4e08-ad08-6ba1336dd9c9" />

```sql
select * from CUSTOMERS
where salary=1500;
```

**Output:**

<img width="1202" height="314" alt="image" src="https://github.com/user-attachments/assets/b0f59f1a-bc25-4daa-9a5f-d60bc4c0476e" />


**Question 4**
<img width="1034" height="506" alt="image" src="https://github.com/user-attachments/assets/39db772a-39df-4de1-8cff-1ec0de71d2db" />


```sql
select medication_id as medic, medication_name, dosage from Medications
where dosage=(
select max(dosage) as 'dosage' from Medications);
```

**Output:**

<img width="875" height="383" alt="image" src="https://github.com/user-attachments/assets/a71eb63c-fb1f-4f33-8224-bf7a790d8011" />


**Question 5**
<img width="1057" height="630" alt="image" src="https://github.com/user-attachments/assets/bd091d90-3cc9-46db-9b58-500c131d3945" />


```sql
select * from CUSTOMERS 
where address='Delhi' and age<30
order by id asc;
```

**Output:**

<img width="1207" height="350" alt="image" src="https://github.com/user-attachments/assets/41284a36-2b33-4554-bb3d-1b84330df8e8" />


**Question 6**
<img width="1091" height="559" alt="image" src="https://github.com/user-attachments/assets/6117ca0f-0eed-451d-b1ee-bdc566810d50" />

```sql
select name from customer
where phone in(
select phone from customer
group by phone
having count(*) = 1);
```

**Output:**

<img width="467" height="442" alt="image" src="https://github.com/user-attachments/assets/5874a9da-1a52-4a19-a5ae-726965fc62f7" />


**Question 7**
<img width="982" height="739" alt="image" src="https://github.com/user-attachments/assets/0faf6e96-7b96-43d3-b379-464af70e5a75" />

```sql
select * from CUSTOMERS
where salary>1500;
```

**Output:**

<img width="1214" height="598" alt="image" src="https://github.com/user-attachments/assets/5a3edd3e-d9b9-4673-8959-b00fbb14945c" />


**Question 8**
<img width="1045" height="700" alt="image" src="https://github.com/user-attachments/assets/83ed5b80-be99-4424-81d5-ffadce38d36c" />


```sql
select * from CUSTOMERS
where salary>4500;
```

**Output:**

<img width="1211" height="413" alt="image" src="https://github.com/user-attachments/assets/b3fdb8f4-53ba-4cd1-b2ed-bb867bce1ec2" />

**Question 9**
<img width="1147" height="674" alt="image" src="https://github.com/user-attachments/assets/f030c672-2d2d-4c43-9834-e00bf2914282" />


```sql
select * from Employee
where age<(
select avg(age) as age from employee
where income>250000);
```

**Output:**

<img width="1246" height="443" alt="image" src="https://github.com/user-attachments/assets/7897f7f0-d161-4580-8bf9-bf17a203dc6a" />


**Question 10**
<img width="1251" height="657" alt="image" src="https://github.com/user-attachments/assets/1be3826e-8fbd-4c8a-ac27-2742d7f3adb1" />


```sql
select student_name, grade from GRADES
where grade=(
select min(grade) from GRADES as g
where g.subject=GRADES.subject);
```

**Output:**

<img width="753" height="408" alt="image" src="https://github.com/user-attachments/assets/fd2cf1f3-70bd-4d51-b08b-10651cb85ca2" />


## RESULT
Thus, the SQL queries to implement subqueries and views have been executed successfully.
