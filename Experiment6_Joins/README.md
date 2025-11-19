# Experiment 6: Joins

## AIM
To study and implement different types of joins.

## THEORY

SQL Joins are used to combine records from two or more tables based on a related column.

### 1. INNER JOIN
Returns records with matching values in both tables.

**Syntax:**
```sql
SELECT columns
FROM table1
INNER JOIN table2
ON table1.column = table2.column;
```

### 2. LEFT JOIN
Returns all records from the left table, and matched records from the right.

**Syntax:**

```sql
SELECT columns
FROM table1
LEFT JOIN table2
ON table1.column = table2.column;
```
### 3. RIGHT JOIN
Returns all records from the right table, and matched records from the left.

**Syntax:**

```sql
SELECT columns
FROM table1
RIGHT JOIN table2
ON table1.column = table2.column;
```
### 4. FULL OUTER JOIN
Returns all records when there is a match in either left or right table.

**Syntax:**

```sql
SELECT columns
FROM table1
FULL OUTER JOIN table2
ON table1.column = table2.column;
```

**Question 1**
--
<img width="1262" height="889" alt="image" src="https://github.com/user-attachments/assets/de32f904-ab83-4b0f-8198-8e79300878bb" />


```sql
SELECT 
    c.cust_name AS "Customer Name",
    c.city AS "city",
    s.name AS "Salesman",
    s.city AS "city",
    s.commission
FROM customer c
JOIN salesman s 
    ON c.salesman_id = s.salesman_id
WHERE c.city <> s.city     
  AND s.commission > 0.12;  

```

**Output:**

<img width="1274" height="492" alt="image" src="https://github.com/user-attachments/assets/b19eaee8-3a08-4f24-8fca-3ba25b365fb3" />


**Question 2**
---
<img width="1247" height="824" alt="image" src="https://github.com/user-attachments/assets/22e38e93-8203-476a-a19f-c62ac5344570" />

```sql
SELECT 
    p.admission_date,
    s.surgery_date
FROM patients p
INNER JOIN surgeries s
    ON p.patient_id = s.patient_id;

```

**Output:**

<img width="744" height="522" alt="image" src="https://github.com/user-attachments/assets/045b7c12-191f-42ea-9dcc-c2bb7b638cdb" />


**Question 3**
---
<img width="1212" height="802" alt="image" src="https://github.com/user-attachments/assets/ca586d7b-c593-4965-8a96-d7a5df983d0f" />


```sql
SELECT 
    p.first_name AS patient_name,
    d.specialization AS Doctor_specialization
FROM patients p
INNER JOIN doctors d
    ON p.doctor_id = d.doctor_id
WHERE p.admission_date BETWEEN '2024-01-01' AND '2024-01-31';

```

**Output:**
<img width="727" height="374" alt="image" src="https://github.com/user-attachments/assets/7f08306e-601e-4809-a404-8ac37bf98ebc" />


**Question 4**
---
<img width="1056" height="907" alt="image" src="https://github.com/user-attachments/assets/c413b82f-ab57-417f-8cf5-df27cbf3b15c" />


```sql
SELECT
    s.name AS Salesman,
    c.cust_name,
    c.city
FROM salesman s
JOIN customer c
    ON s.city = c.city
ORDER BY s.salesman_id, c.cust_name;

```

**Output:**

<img width="1053" height="673" alt="image" src="https://github.com/user-attachments/assets/507723b0-77d9-4cff-8b25-434d2b4c100a" />


**Question 5**
---
<img width="928" height="978" alt="image" src="https://github.com/user-attachments/assets/0b57ba72-7ff8-47e2-bed2-1eae19d4aaea" />

```sql
SELECT
    o.ord_no,
    o.ord_date,
    o.purch_amt,
    c.cust_name AS "Customer Name", 
    c.grade,                      
    s.name AS Salesman,            
    s.commission                   
FROM
    orders o 
INNER JOIN
    customer c
    ON o.customer_id = c.customer_id 
INNER JOIN
    salesman s  
    ON o.salesman_id = s.salesman_id; 
```

**Output:**

<img width="1332" height="796" alt="image" src="https://github.com/user-attachments/assets/efdb0e2a-08b1-4534-a393-5a5e85050df5" />


**Question 6**
---
<img width="1249" height="794" alt="image" src="https://github.com/user-attachments/assets/f3d7a510-9c55-4aa2-adf0-0593ba78c85c" />


```sql
SELECT 
    p.first_name,
    s.*
FROM patients p
INNER JOIN surgeries s
    ON p.patient_id = s.patient_id
WHERE p.first_name = 'Alice';

```

**Output:**

<img width="1280" height="313" alt="image" src="https://github.com/user-attachments/assets/66308922-4813-4ee0-9dc9-fca027a4d983" />


**Question 7**
---
<img width="1260" height="888" alt="image" src="https://github.com/user-attachments/assets/8d7ffda0-994e-4f31-bae5-d4431ab542f9" />


```sql
SELECT 
    o.ord_no,
    o.purch_amt,
    c.cust_name,
    c.city
FROM 
    orders o
JOIN 
    customer c
ON 
    o.customer_id = c.customer_id
WHERE 
    o.purch_amt BETWEEN 500 AND 2000;

```

**Output:**

<img width="1230" height="405" alt="image" src="https://github.com/user-attachments/assets/469c9af7-1443-4b84-806a-c1674c396141" />


**Question 8**
---
<img width="1257" height="366" alt="image" src="https://github.com/user-attachments/assets/9f6b6798-69d0-4f73-9a76-eda173469928" />


```sql
SELECT c.cust_name
FROM customer c
LEFT JOIN orders o
    ON c.customer_id = o.customer_id
WHERE o.purch_amt < 100;

```

**Output:**

<img width="426" height="449" alt="image" src="https://github.com/user-attachments/assets/9a232930-cbef-4f0a-a908-470ab5aa2271" />


**Question 9**
---
<img width="1270" height="521" alt="image" src="https://github.com/user-attachments/assets/79de8bc2-312b-48eb-8e62-01131ff6be32" />



```sql
select c.cust_name, s.commission from customer c left join salesman s
on c.salesman_id=s.salesman_id;
```

**Output:**
<img width="724" height="888" alt="image" src="https://github.com/user-attachments/assets/fc64d398-cd55-497d-9756-c65acc237279" />


**Question 10**
---
<img width="1217" height="658" alt="image" src="https://github.com/user-attachments/assets/d69c1edf-daf6-4a26-b126-7a40954e04ca" />


```sql
SELECT c.cust_name
FROM customer c
LEFT JOIN orders o
    ON c.customer_id = o.customer_id;

```

**Output:**

<img width="355" height="955" alt="image" src="https://github.com/user-attachments/assets/7467759d-becf-42e2-a274-41ff8c4ec10c" />



## RESULT
Thus, the SQL queries to implement different types of joins have been executed successfully.
