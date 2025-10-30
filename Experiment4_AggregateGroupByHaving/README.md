# Experiment 4: Aggregate Functions, Group By and Having Clause

## AIM
To study and implement aggregate functions, GROUP BY, and HAVING clause with suitable examples.

## THEORY

### Aggregate Functions
These perform calculations on a set of values and return a single value.

- **MIN()** – Smallest value  
- **MAX()** – Largest value  
- **COUNT()** – Number of rows  
- **SUM()** – Total of values  
- **AVG()** – Average of values

**Syntax:**
```sql
SELECT AGG_FUNC(column_name) FROM table_name WHERE condition;
```
### GROUP BY
Groups records with the same values in specified columns.
**Syntax:**
```sql
SELECT column_name, AGG_FUNC(column_name)
FROM table_name
GROUP BY column_name;
```
### HAVING
Filters the grouped records based on aggregate conditions.
**Syntax:**
```sql
SELECT column_name, AGG_FUNC(column_name)
FROM table_name
GROUP BY column_name
HAVING condition;
```

**Question 1**
--
<img width="910" height="601" alt="image" src="https://github.com/user-attachments/assets/b1a979fd-8493-4d11-9aa5-c978816b79df" />


```sql
select DoctorID, count(*) as
TotalPrescriptions
from Prescriptions
group by DoctorID;
```

**Output:**

<img width="621" height="661" alt="image" src="https://github.com/user-attachments/assets/36ed53fe-c3a8-493d-9aea-c1c5cc83b094" />


**Question 2**
---
<img width="939" height="581" alt="image" src="https://github.com/user-attachments/assets/bc6edc6d-74f0-4e08-a4c3-a51d77bf64a9" />


```sql
select 
  Medication,
  Avg(Dosage) as AvgDosage
from 
  Prescriptions
group by 
  Medication;
```

**Output:**

<img width="568" height="663" alt="image" src="https://github.com/user-attachments/assets/75942895-7ca7-4d56-806c-9bd026732e63" />


**Question 3**
---
<img width="646" height="593" alt="image" src="https://github.com/user-attachments/assets/137a8159-903c-4309-8738-65b30a9bb9ad" />


```sql
select DATE(AppointmentDateTime) as AppointmentDate, count(AppointmentID) as TotalAppointments
from Appointments
group by AppointmentDate;
```

**Output:**

<img width="695" height="579" alt="image" src="https://github.com/user-attachments/assets/7e0c1abe-51b8-4bce-9f64-1bc619e0070a" />


**Question 4**
---
<img width="871" height="452" alt="image" src="https://github.com/user-attachments/assets/6b2dcba1-7c88-4c9c-a774-dc2a1fb45732" />

```sql
SELECT COUNT(*) AS COUNT
FROM customer
WHERE city <> 'Noida';
```

**Output:**

<img width="327" height="267" alt="image" src="https://github.com/user-attachments/assets/5d8cd0da-2d35-4e54-a532-951382f244f7" />

**Question 5**
---
<img width="781" height="424" alt="image" src="https://github.com/user-attachments/assets/ea72b3ac-cc07-430e-adf9-9696c3a179b9" />

```sql
select avg(income) as
avg_income
from employee
where name LIKE 'A%';
```

**Output:**

<img width="338" height="268" alt="image" src="https://github.com/user-attachments/assets/bccbad9f-1a93-4ade-989b-77c68c106345" />


**Question 6**
---
<img width="705" height="451" alt="image" src="https://github.com/user-attachments/assets/5a693b52-f538-4349-a56b-52e7c26021f0" />


```sql
select 
  name as Employee_Name,
  age as Age
from 
  employee
order by 
  age ASC
limit 1;
```

**Output:**

<img width="598" height="266" alt="image" src="https://github.com/user-attachments/assets/bd4bcfcc-4f38-4e03-bd2f-c52095d0a980" />


**Question 7**
---
<img width="766" height="442" alt="image" src="https://github.com/user-attachments/assets/4d14442d-42b1-4643-b74e-66a4f75fcec0" />

```sql
select count(Distinct city) as
unique_cities
from customer;
```

**Output:**

<img width="390" height="260" alt="image" src="https://github.com/user-attachments/assets/3eda8b23-ce9f-415b-bdbe-3cf70c37107e" />

**Question 8**
---
<img width="1228" height="448" alt="image" src="https://github.com/user-attachments/assets/c65a62e4-bd41-48e3-873f-8b201ca84c8f" />


```sql
select category_id, sum(price) as Total_Cost
from products
group by category_id
having sum(price)>50;
```

**Output:**
<img width="546" height="291" alt="image" src="https://github.com/user-attachments/assets/dad821a6-7425-462a-acbd-9cd6ec15e4f2" />


**Question 9**
---
<img width="1221" height="451" alt="image" src="https://github.com/user-attachments/assets/e2fe926c-0db6-49cb-8f5b-6e0606ce9991" />


```sql
select category_id, count(product_name) as COUNT
from products
where category_id>2
group by category_id;
```

**Output:**

<img width="531" height="288" alt="image" src="https://github.com/user-attachments/assets/f9ad8f02-5eef-42f3-94ea-750a82eb4905" />


**Question 10**
---
<img width="1233" height="457" alt="image" src="https://github.com/user-attachments/assets/0b39323d-73b8-4bb9-be6e-edbcd22d6368" />


```sql
select occupation, AVG(workhour)
from employee1
group by occupation
having AVG(workhour) between 10 and 12;
```

**Output:**

<img width="560" height="328" alt="image" src="https://github.com/user-attachments/assets/bfef6aee-125d-4061-a2bc-e0d5815435e0" />



## RESULT
Thus, the SQL queries to implement aggregate functions, GROUP BY, and HAVING clause have been executed successfully.
