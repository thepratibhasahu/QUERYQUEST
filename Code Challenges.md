# Code Challenges

The `babies` table has the following columns:

* `name` - the name of the baby
* `year` - the year the name was given
* `gender` - the gender of the baby
* `number` - the number of times the name was given

→  Table diagram

<img width="648" height="410" alt="image" src="https://github.com/user-attachments/assets/fd16ed51-4201-435c-8b0a-6b36ab9e928b" />

**(1.)** Find the number of girls who were named Lillian for the full span of time of the database.         
Select only the `year` and `number` columns.
```sql
SELECT year, number
FROM babies
WHERE name = 'Lillian';
```
### 🟩Output
```sql
+------+--------+
| year | number |
+------+--------+
| 1880 |   672  |
| 1881 |   723  |
+------+--------+
```
**(2.)** Find 20 distinct names that start with `‘S’`.                            
Select only the `name` column.
```SQL
SELECT DISTINCT name
FROM babies
WHERE name LIKE 'S%'
LIMIT 20;
```
### 🟩Output
```SQL
+------------+
|   name     |
+------------+
|   Sarah    |
|   Stella   |
|   Sallie   |
|   Susie    |
|   Sadie    |
|   Susan    |
|   Sara     |
|   Sophia   |
|   Sophie   |
|   Sylvia   |
|   Sally    |
|   Sue      |
|   Selma    |
|   Sudie    |
| Samantha   |
| Susanna    |
| Savannah   |
|  Sidney    |
| Sophronia  |
|  Serena    |
+------------+
```
**(3.)** What are the top 10 names in 1880?                      
Select the `name`, `gender`, and number `columns`.
```SQL
SELECT name, gender, number
FROM babies
WHERE year = 1880
ORDER BY number DESC
LIMIT 10;
```
### 🟩Output
```sql
+---------+--------+--------+
|  name   | gender | number |
+---------+--------+--------+
|  John   |   M    |  9655  |
| William |   M    |  9532  |
|  Mary   |   F    |  7065  |
| James   |   M    |  5927  |
| Charles |   M    |  5348  |
| George  |   M    |  5126  |
| Frank   |   M    |  3242  |
| Joseph  |   M    |  2632  |
|  Anna   |   F    |  2604  |
| Thomas  |   M    |  2534  |
+---------+--------+--------+
```
# Restaurants Introduction

Next up, you will be querying data on restaurants:

* Baby Names
* **Restaurants**
* News Headlines

We need your help to answer some questions and find the best dinner spots in the city!                  

You’ll work with a table named `nomnom` with six columns.

→  Table diagram

<img width="627" height="324" alt="image" src="https://github.com/user-attachments/assets/42e7cc6d-e97e-423b-882f-c1b9a6b238a6" />

The nomnom table has the following columns:

* `name` - the restaurant name
* `neighborhood` - the neighborhood name
* `cuisine` - the cuisine type
* `review` - the average user review
* `price` - the price range
* `health` - the health inspection grade

**(1.)** Suppose your friend Jaime wants to go out to Japanese, but you’re on a budget.                      
Return all the restaurants that are `Japanese` and `$$`.                                 
Select all the columns.
```sql
SELECT *
FROM nomnom
WHERE cuisine = 'Japanese'
  AND price = '$$';
```
### 🟩Output
```sql
+--------+--------------+----------+--------+-------+--------+
|  name  | neighborhood | cuisine  | review | price | health |
+--------+--------------+----------+--------+-------+--------+
| Minca  | Downtown     | Japanese |  4.4   |  $$   |   A    |
| Ippudo | Downtown     | Japanese |  4.4   |  $$   |   A    |
| Ootoya | Downtown     | Japanese |  4.5   |  $$   |   A    |
+--------+--------------+----------+--------+-------+--------+
```
**(2.)** Your roommate Bevers can’t remember the exact name of a restaurant he went to but he knows it contains the word ‘noodle’ in it.                                  
Can you find it for him using a query?                                   
Select all the columns.
```sql
SELECT * FROM nomnom
WHERE name LIKE '%noodle%';
```
### 🟩Output
```sql
+------------------------+--------------+---------+--------+-------+--------+
|         name           | neighborhood | cuisine | review | price | health |
+------------------------+--------------+---------+--------+-------+--------+
| Great NY Noodletown    | Chinatown    | Chinese |  4.1   |  $$   |   B    |
+------------------------+--------------+---------+--------+-------+--------+
```
**(3.)** Some of the restaurants have not been inspected yet or are currently appealing their health grade score.   
Find the restaurants that have empty `health` values.                           
Select all the columns.































































