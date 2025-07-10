# Code Challenge 1

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
