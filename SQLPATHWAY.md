# A Day in the Life - Data Analyst

It’s Catherine’s first day working as a Data Analyst for Codecademy. She’s excited to use some of the tools that she learned in **Analyze Data with SQL**, such as:

* Writing basic queries
* Calculating aggregates
* Combining data from multiple tables
* Determining web traffic attribution
* Creating usage funnels
* Analyzing user churn

# Exploring Data with SQL

Like most organizations, Codecademy uses **SQL** `(Structured Query Language)` to access its database.

A `database` is a set of data stored in a computer. This data is usually structured into tables. Tables can grow large and have a multitude of columns and records.

Spreadsheets, like Microsoft Excel and Google Sheets, allow you to view and manipulate data directly: with selecting, filtering, sorting, etc. By applying a number of these operations you can obtain the subset of data you are seeking.

SQL (pronounced “S-Q-L” or “sequel”) allows you to write `queries` which define the subset of data you are seeking. Unlike Excel and Sheets, your computer and SQL will handle how to get the data; you can focus on what data you would like. You can save these queries, refine them, share them, and run them on different databases.

It is a great way to access data and a great entry point to programming because its syntax (the specific vocabulary that gives instructions to the computer) is very human-readable. Without knowing any SQL, you might still be able to guess what each command will do.

On her first day at Codecademy, Catherine wants to become familiar with the company’s data, so she connects to the database and uses SQL to explore the database.

**(1.)** One of the tables in Codecademy’s database is called `browse`. It contains information on each time someone visited the Codecademy’s website. Paste the following code into the code editor (middle panel) and click Run.
```sql
SELECT *
FROM browse
LIMIT 10;
```
* This code will select all (`*`) columns from `browse` for the first 10 records.
* Enter the correct code and click “Run”. Once complete, click “Next” to go to the next exercise.

### 🟩Output
```sql
                 user_id                        browse_date  item_id
     336f9fdc-aaeb-48a1-a773-e3a935442d45       2017-12-20      3
     336f9fdc-aaeb-48a1-a773-e3a935442d45       2017-12-20     22
     336f9fdc-aaeb-48a1-a773-e3a935442d45       2017-12-20     25
     336f9fdc-aaeb-48a1-a773-e3a935442d45       2017-12-20     24
     4596bb1a-7aa9-4ac9-9896-022d871cdcde       2017-12-20      0
     4596bb1a-7aa9-4ac9-9896-022d871cdcde       2017-12-20      2
     2fdb3958-ffc9-4b84-a49d-5f9f40e9469e       2017-12-20     26
     2fdb3958-ffc9-4b84-a49d-5f9f40e9469e       2017-12-20     24
     fc394c75-36f1-4df1-8665-23c32a43591b       2017-12-20     12
     fc394c75-36f1-4df1-8665-23c32a43591b       2017-12-20     24
```








