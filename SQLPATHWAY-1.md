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
# Creating Usage Funnels
Visitors to Codecademy’s website follow a simple workflow:

* Browse items available for sale
* Click an icon to begin the checkout process
* Enter payment information to complete their purchase

Not all users who browse on the website will find something that they like enough to checkout, and not all users who begin the checkout process will finish entering their payment information to make a purchase.

This type of multi-step process where some users leave at each step is called a funnel.

Catherine wants to determine what percent of users make it through each step of the funnel so that she can recommend improvements to Codecademy’s website.

**(1.)** Catherine is going to combine data from three different tables:

* `browse` - gives the timestamps of users who visited different item description pages
* `checkout` - gives the timestamps of users who visited the checkout page
* `purchase` - gives the timestamps of when users complete their purchase

Using SQL, she finds that 24% of all users who browse move on to checkout. 89% of those who reach checkout purchase.  
Click Run, to see Catherine’s analysis.
```sql
SELECT ROUND(
   100.0 * COUNT(DISTINCT c.user_id) /
   COUNT(DISTINCT b.user_id)
 ) AS browse_to_checkout_percent,
 ROUND(
   100.0 * COUNT(DISTINCT p.user_id) /
   COUNT(DISTINCT c.user_id)
 ) AS checkout_to_purchase_percent
 FROM browse b
 LEFT JOIN checkout c
 	ON b.user_id = c.user_id
 LEFT JOIN purchase p
 	ON c.user_id = p.user_id;
```
→ In the result, there should be two columns:

* `browse_to_checkout_percent`
* `checkout_to_purchase_percent`

### 🟩Output
```sql
+-----------------------------+------------------------------+
| browse_to_checkout_percent | checkout_to_purchase_percent |
+-----------------------------+------------------------------+
|            24.0            |             89.0             |
+-----------------------------+------------------------------+
```
# Analyzing User Churn
Next, Catherine wants to take a look at the churn rate.

A churn rate is the percent of subscribers to a monthly service who have canceled. For example, in January, let’s say Codecademy has 1,000 customers. In February, 200 learners sign up, and 250 cancel.

The churn rate for February would be:

<img width="275" alt="image" src="https://github.com/user-attachments/assets/39a15721-7b29-45a1-ba8d-f35979ec9963" />

Catherine wants to analyze the churn rates for Codecademy for the past few months so she writes another SQL query.

**(1.)** Click Run, to see Catherine’s analysis for the churn rate in March 2017.                  
What recommendations would you make to Codecademy based on Catherine’s analysis?                     
(This query might take some time to load because the `pro_users` table has 118,135 rows!)
```sql
SELECT COUNT(DISTINCT user_id) AS enrollments,
	COUNT(CASE
       	WHEN strftime("%m", cancel_date) = '03'
        THEN user_id
  END) AS march_cancellations,
 	ROUND(100.0 * COUNT(CASE
       	WHEN strftime("%m", cancel_date) = '03'
        THEN user_id
  END) / COUNT(DISTINCT user_id)) AS churn_rate
FROM pro_users
WHERE signup_date < '2017-04-01'
	AND (
    (cancel_date IS NULL) OR
    (cancel_date > '2017-03-01')
  );
```
In the result, there should be three columns:

* `enrollments`
* `march_cancellations`
* `churn_rate`
### 🟩Output
```sql
+--------------+----------------------+------------+
| enrollments  | march_cancellations  | churn_rate |
+--------------+----------------------+------------+
|    16435     |        4165          |    25.0    |
+--------------+----------------------+------------+
```
# Determining Web Traffic Attribution
Catherine’s boss asks her to analyze how users are finding Codecademy’s websites using UTM Parameters. UTM Parameters are special tags that site owners add to their pages to track what website a user was on before they reach the website. For instance:

* If a user found Codecademy’s website through Google search, the table `page_visits` might have `utm_source` set to ‘google’.
* If a different user clicked a Facebook ad to get to Codecademy’s website, then their row in `page_visits` might have `utm_source` as ‘facebook’.

**(1.)** Catherine wants to know how many visits come from each `utm_source`.                          
Click Run, to see Catherine’s analysis.                          
What is the most common source of traffic to Codecademy’s website?
```sql
 SELECT utm_source,
 	COUNT(DISTINCT user_id) AS num_users
FROM page_visits
GROUP BY 1
ORDER BY 2 DESC;
```
### 🟩Output
```sql
+------------+------------+
| utm_source | num_users |
+------------+------------+
|  nytimes   |    747     |
|   email    |    696     |
| buzzfeed   |    648     |
|  medium    |    625     |
| facebook   |    445     |
|  google    |    339     |
+------------+------------+
```


