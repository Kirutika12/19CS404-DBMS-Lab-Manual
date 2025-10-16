# Experiment 3: DML Commands

## AIM
To study and implement DML (Data Manipulation Language) commands.

## THEORY

### 1. INSERT INTO
Used to add records into a relation.
These are three type of INSERT INTO queries which are as
A)Inserting a single record
**Syntax (Single Row):**
```sql
INSERT INTO table_name (field_1, field_2, ...) VALUES (value_1, value_2, ...);
```
**Syntax (Multiple Rows):**
```sql
INSERT INTO table_name (field_1, field_2, ...) VALUES
(value_1, value_2, ...),
(value_3, value_4, ...);
```
**Syntax (Insert from another table):**
```sql
INSERT INTO table_name SELECT * FROM other_table WHERE condition;
```
### 2. UPDATE
Used to modify records in a relation.
Syntax:
```sql
UPDATE table_name SET column1 = value1, column2 = value2 WHERE condition;
```
### 3. DELETE
Used to delete records from a relation.
**Syntax (All rows):**
```sql
DELETE FROM table_name;
```
**Syntax (Specific condition):**
```sql
DELETE FROM table_name WHERE condition;
```
### 4. SELECT
Used to retrieve records from a table.
**Syntax:**
```sql
SELECT column1, column2 FROM table_name WHERE condition;
```
**Question 1**
<img width="934" height="551" alt="image" src="https://github.com/user-attachments/assets/249c1da2-7a68-4377-a38d-7b21ce981ba8" />


```
select ename 
from emp 
where lower(substr(ename, 1,2)) = lower(substr(ename,length(ename) - 1,2));
```

**Output:**

<img width="482" height="305" alt="image" src="https://github.com/user-attachments/assets/839b8ef5-521b-4a83-8b85-e0204de14b73" />


**Question 2**
<img width="1000" height="710" alt="image" src="https://github.com/user-attachments/assets/f1fb7e6c-eaf4-42d4-9c5a-c1d49c297467" />


```
select ename, hiredate,
  case strftime('%w', hiredate)
    when '0' then 'Sunday'
    when '1' then 'Monday'
    when '2' then 'Tuesday'
    when '3' then 'Wednesday'
    when '4' then 'Thursday'
    when '5' then 'Friday'
    when '6' then 'Saturday'
  end as day_of_week
from emp;  
```

**Output:**

<img width="809" height="353" alt="image" src="https://github.com/user-attachments/assets/420cddf9-f73d-476c-9a1e-f08ef025ef96" />

**Question 3**
<img width="1086" height="493" alt="image" src="https://github.com/user-attachments/assets/2cbed97f-064d-406c-9bab-1331996d8424" />

```
select product_id, original_price, discount_percentage, original_price-(original_price*discount_percentage) as discounted_price
from Products;
```

**Output:**
<img width="1195" height="368" alt="image" src="https://github.com/user-attachments/assets/02aa4b35-d595-47bb-92ee-65c28831c1bf" />

**Question 4**
<img width="1228" height="338" alt="image" src="https://github.com/user-attachments/assets/ba0afcbf-0d47-4a5c-9542-ff13748adc07" />

```
select product_id,original_price,discount_percentage,original_price*(1-discount_percentage) as discounted_price
from products
where original_price*(1-discount_percentage) between 100 and 250;
```

**Output:**
<img width="1202" height="231" alt="image" src="https://github.com/user-attachments/assets/c49c4aa4-3479-4a4a-a2a7-b084e31ca0fd" />


**Question 5**
<img width="1147" height="451" alt="image" src="https://github.com/user-attachments/assets/41466e13-b91d-46ad-bc6c-110eefdf9ee7" />


```
select customer_id,cust_name,city,grade,salesman_id from customer where city='New York' or grade<=100 or grade is NULL;
```

**Output:**
<img width="1165" height="369" alt="image" src="https://github.com/user-attachments/assets/871874dc-6027-436f-9a6a-fb1f57cadffa" />


**Question 6**

<img width="768" height="528" alt="image" src="https://github.com/user-attachments/assets/e7329269-dbe0-4ca4-bdc1-118539d21596" />


```
select id, Round(decimal,3) as rounded_value from Calculations;
```

**Output:**

<img width="610" height="249" alt="image" src="https://github.com/user-attachments/assets/4e7fa8b3-8950-4de9-b522-278c313e1d45" />


**Question 7**

<img width="1233" height="558" alt="image" src="https://github.com/user-attachments/assets/a7cff6f1-dfbc-4766-8f11-5f0067e6be50" />


```
select id,value2,
   case
      when value2<30 then 'Poor'
      when value2 between 30 and 70 then 'Average'
      when value2>70 then 'Excellent'
    end as performance
from Calculations;    
```

**Output:**

<img width="787" height="375" alt="image" src="https://github.com/user-attachments/assets/164d119f-3af3-4adc-955f-4d281e54cf99" />

**Question 8**

<img width="745" height="500" alt="image" src="https://github.com/user-attachments/assets/b94c9bbb-0330-4fbf-b322-a812e2acc939" />


```
select patient_id, first_name, admission_date from Patients where admission_date between "2023-01-01" and "2023-12-31";
```

**Output:**

<img width="753" height="282" alt="image" src="https://github.com/user-attachments/assets/d8a20cda-3c1e-4c9f-a90a-64bbda6d537d" />

**Question 9**

<img width="843" height="455" alt="image" src="https://github.com/user-attachments/assets/7da42faa-bc41-4490-9b0e-b7276b617267" />

```
delete from Customer where GRADE!=3;
```

**Output:**

<img width="1170" height="319" alt="image" src="https://github.com/user-attachments/assets/3a8d9c5c-7a6d-4652-8429-0796e690fcd6" />

**Question 10**

<img width="891" height="461" alt="image" src="https://github.com/user-attachments/assets/457bae1c-c913-42f8-9ce5-c7409b47acd2" />


```
delete from Surgeries where surgery_date="2024-02-28";
```

**Output:**

<img width="1170" height="319" alt="image" src="https://github.com/user-attachments/assets/773ab541-0b01-4beb-939a-5c9c882b7504" />



## RESULT
Thus, the SQL queries to implement DML commands have been executed successfully.
