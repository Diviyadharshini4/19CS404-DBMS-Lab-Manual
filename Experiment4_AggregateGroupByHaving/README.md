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
-- How many male and female doctors are there in each medical specialty?

Sample table:Doctors Table For example:

Result Specialty Gender TotalDoctors

Cardiology Male 1 Dermatology Male 1 Gastroenterology Female 4 Gastroenterology Male 1 Pediatrics Female 1 Pediatrics Male 2
```
SELECT Specialty,Gender,count(*) as TotalDoctors
from Doctors
group by Specialty,Gender
order by Specialty,Gender;
```

**Output:**

<img width="857" height="632" alt="image" src="https://github.com/user-attachments/assets/9bfa0e7e-afde-4375-9a56-8ecbc10252b8" />


**Question 2**
---
-- Write the SQL query that achieves the grouping of data by city, calculates the total income for each city, and includes only those cities where the total income sum is greater than 200,000.

Sample table: employee For example:

Result city Income

Alaska 450000 Arizona 1000000 California 5300000 Florida 5350000 Georgia 250000 here
```
SELECT city, sum(income) as Income from employee
group by city having Income > 200000;
```

**Output:**
<img width="815" height="761" alt="image" src="https://github.com/user-attachments/assets/2f5ec077-0211-4297-81e8-8017836d1706" />


**Question 3**
---
--Write the SQL query that achieves the grouping of data by occupation, calculates the minimum work hours for each occupation, and excludes occupations where the minimum work hour is not greater than 8.

Sample table: employee1

For example:

Result occupation MIN(workhour)

Business 10 Doctor 15 Engineer 12 Teacher 9

```
SELECT occupation,  AVG(workhour) from employee1
group by occupation having AVG(workhour) between 10 and 12;
```

**Output:**

<img width="800" height="590" alt="image" src="https://github.com/user-attachments/assets/2b3675f3-b17d-41ba-955a-a72f89de0098" />


**Question 4**
---
-- Write the SQL query that achieves the grouping of data by occupation, calculates the average work hours for each occupation, and includes only those occupations where the average work hour falls between 10 and 12.

Sample table: employee1

For example:

Result occupation AVG(workhour)

Business 10.0 Engineer 12.0

```
-- SELECT occupation,  AVG(workhour) from employee1
group by occupation having AVG(workhour) between 10 and 12;
```

**Output:**
<img width="829" height="593" alt="image" src="https://github.com/user-attachments/assets/2f7e3a69-a6fa-4cee-a7be-24a7466c7a17" />


**Question 5**
---
--Write a SQL query to find the average length of names for people living in Chennai?

Table: customer

name type

id INTEGER name TEXT
city TEXT email TEXT phone INTEGER For example:

Result avg_name_length
10.0

```
SELECT avg(length(name)) as avg_name_length from customer
where city = 'Chennai';

```

**Output:**

<img width="633" height="487" alt="image" src="https://github.com/user-attachments/assets/af790cad-eb7a-4807-b537-dfa69af73688" />


**Question 6**
---
--Write a SQL query to find the minimum purchase amount.

Sample table: orders

ord_no purch_amt ord_date customer_id salesman_id

70001 150.5 2012-10-05 3005 5002

70009 270.65 2012-09-10 3001 5005

70002 65.26 2012-10-05 3002 5001

For example:

Result MINIMUM
```65.26
SELECT min(purch_amt) as MINIMUM FROM orders
order by MINIMUM ASC LIMIT 1;
```

**Output:**

<img width="635" height="486" alt="image" src="https://github.com/user-attachments/assets/8a60e21b-a583-41a8-b513-f0bad22fde16" />


**Question 7**
---
-- Write a SQL query to find the shortest email address in the customer table?

Table: customer

name type

id INTEGER name TEXT
city TEXT email TEXT phone INTEGER For example:

Result name email min_email_length

Ravi Kumar ravi@gmail.com 14

```
SELECT name,email, length(email) as min_email_length
from customer
order by length(email) asc
limit 1;
```

**Output:**

<img width="850" height="307" alt="image" src="https://github.com/user-attachments/assets/b6ab48d7-21ef-4abb-9793-c153574305b4" />


**Question 8**
---
-- Write a SQL query to find the Fruit with the lowest available quantity.

Note: Inventory attribute contains amount of fruits

Table: fruits

name type

id INTEGER name TEXT unit TEXT inventory INTEGER price REAL

For example:

Result fruit_name lowest_quantity

Watermelon 15

```
SELECT name as fruit_name, inventory as lowest_quantity from fruits
order by inventory asc limit 1;
```

**Output:**

<img width="851" height="470" alt="image" src="https://github.com/user-attachments/assets/a7aff928-5ff5-4689-97c6-0c1daab9a439" />


**Question 9**
---
-- How many prescriptions were written in each frequency category (e.g., once daily, twice daily)?

Sample tablePrescriptions Table

For example:

Result Frequency TotalPrescriptions

Every 3 weeks 1 Every 6 hours 1 Once 1 Once daily 4 Once daily at 1 Pending 1 Twice daily 1

```
SELECT Frequency,count(*) as TotalPrescriptions 
from Prescriptions
group by Frequency  
order by Frequency ;
```

**Output:**

<img width="852" height="680" alt="image" src="https://github.com/user-attachments/assets/fa0df195-4dea-44b6-b8d6-b74ac69250dd" />


**Question 10**
---
-- Write a SQL query that counts the number of unique salespeople. Return number of salespeople.

Sample table: orders

ord_no purch_amt ord_date customer_id salesman_id

70001 150.5 2012-10-05 3005 5002

70009 270.65 2012-09-10 3001 5005

70002 65.26 2012-10-05 3002 5001

For example:

Result COUNT
6
```
-- select count(distinct salesman_id) as COUNT
from orders;
```

**Output:**

<img width="664" height="549" alt="image" src="https://github.com/user-attachments/assets/608ca479-a4d5-4b1d-bec2-3f266750b421" />

## RESULT
Thus, the SQL queries to implement aggregate functions, GROUP BY, and HAVING clause have been executed successfully.
