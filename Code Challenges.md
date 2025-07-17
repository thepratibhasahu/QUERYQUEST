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

The `nomnom` table has the following columns:

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
```sql
 SELECT * FROM nomnom
 WHERE health IS NULL;
```
### 🟩Output
```sql
+-------------------+--------------+-----------+--------+-------+--------+
|       name        | neighborhood |  cuisine  | review | price | health |
+-------------------+--------------+-----------+--------+-------+--------+
| Massawa           | Uptown       | Ethiopian |  4.0   |  $$   |  null  |
| Wo Hop            | Chinatown    | Chinese   |  4.2   |  $$   |  null  |
| Jacob's Pickles   | Uptown       | American  |  null  |  $$   |  null  |
| Lighthouse        | Brooklyn     | American  |  4.6   |  $$   |  null  |
| Los Hermanos      | Brooklyn     | Mexican   |  4.4   |   $   |  null  |
+-------------------+--------------+-----------+--------+-------+--------+
```
# News Headlines Introduction
Here is the last dataset of the Code Challenge #1:

* Baby Names
* Restaurants
* **News Headlines**

There is a table called `news` with six columns.

It is full of news article headlines from different publishing companies!

→  Table diagram

<img width="625" height="316" alt="image" src="https://github.com/user-attachments/assets/c6a07dce-5abe-4f77-90d7-e6e0e7e7524d" />

The `news` table has the following columns:

* `id` - the article identifier
* `title` - the article title
* `publisher` - the article publisher
* `category` - the article category
* `timestamp` - the time of publication
* `url` - the article web address

**(1.)** Order the table by `title` (from A-Z).                              
Select only the `title` and `publisher` columns.
```sql
SELECT title, publisher
FROM news
ORDER BY title ASC;
```
### 🟩Output
```sql
+-----------------------------------------------------------------------------------------------------------------------------+-----------------------------------------------+
| title                                                                                                                       | publisher                                     |
+-----------------------------------------------------------------------------------------------------------------------------+-----------------------------------------------+
| 1.6m car recall put GM on a rough road                                                                                      | Boston Globe                                  |
| 10 Things You Need To Know Before The Opening Bell                                                                          | Businessinsider India                         |
| 10 Things You Need To Know This Morning                                                                                     | Business Insider                              |
| 10.7 Billion trips taken on transit in America last year, the most since 1956                                               | Treehugger                                    |
| 13 things we'll miss most about Sbarro                                                                                      | Guyism                                        |
| 24m supply chain savings from banana merger                                                                                 | Supply Chain Standard                         |
| 272 Protesters Have Vanished in Ukraine                                                                                     | Newser                                        |
| 3 Predictions for the New Week                                                                                              | Motley Fool                                   |
| 3 things to watch for as McDonald's fights to boost US sales                                                                | GlobalPost                                    |
| 4 Speed-Reading Apps To Give You Lightning Fast Eyes                                                                        | ReadWrite                                     |
| 4 nations urge US gas exports amid Ukraine crisis                                                                           | Idaho State Journal                           |
| 4.7-Inch 'iPhone Air' Shown Off In New Concept Video                                                                        | Mac Rumors                                    |
| 5 Reasons you should be excited for 'Titanfall'                                                                             | Examiner.com                                  |
| 5 great moments from Episode 1 of 'Cosmos'                                                                                  | Mother Nature Network (blog)                  |
| 5 things you missed: Apple releases iOS 7.1, Tumblr allows updates by phone ...                                             | San Jose Mercury News                         |
| 7 Things You Need To Know About iOS 7.1                                                                                     | ReadWrite                                     |
| 8 Crucial Reasons to Download iOS 7.1 Now                                                                                   | GeekSugar.com                                 |
| 840MB Titanfall Day One Patch is Now Live on Xbox One                                                                       | SegmentNext                                   |
| A "Credible Threat" Approach to Long Run Deterrence of Russian-European ...                                                 | Forbes                                        |
| A Recall Bares GM's Love of Red Tape                                                                                        | Wall Street Journal                           |
| A Secular Bull Market Arises From the 2009 Shadows                                                                          | Investorplace.com                             |
| A Smartwatch Version of Android Is Reportedly Coming Soon                                                                   | TIME                                          |
| A Week After Mt. Gox Collapse, Japan Struggles to Understand Bitcoin                                                        | Moneynews                                     |
| A closer look at Titanfall's not-so-secret weapon: Microsoft's cloud                                                        | Engadget                                      |
| A novel in 90 minutes? It's possible with new speed-reading technology                                                      | New York Daily News                           |
| A week after Mt Gox collapse, Japan struggles to understand ..                                                              | Gulf Times                                    |
| AA and JetBlue end ticketing agreement                                                                                      | Travel Weekly                                 |
| AAA Mich.: Gas prices fall 1 cent over past week                                                                            | Argus Press                                   |
| AAA Michigan: Gas prices fall 1 cent over past week                                                                         | Detroit Free Press                            |
| AAA: Gas prices spring forward                                                                                              | Augusta Free Press                            |
| AAA: Gas prices up another four cents this week                                                                             | Wicked Local Raynham                          |
| AAA: RI gas prices climb another 2 cents                                                                                    | The Providence Journal                        |
| ALL ABOARD THE SPACESHIP OF THE IMAGINATION: Did You Watch The ...                                                          | xoJane                                        |
| ANALYSIS-GM must address recall soon to avoid damage to reputation                                                          | Chicago Tribune                               |
| APTA touts 2013 public transit ridership                                                                                    | RailwayAge Magazine                           |
| AT&T's New Mobile Plans; Apple Wins Smartphone Sales; Spritz Speed Reading                                                  | PC Magazine                                   |
| AUTO: Safety regulators demand recall data from General Motors                                                              | Shelby Township Source Newspapers             |
| Accounting News Roundup: Sbarro is Bankrupt (Again); PwC's Latest Buy ...                                                   | Going Concern                                 |
| Ackman Bets $1 Billion on Herbalife                                                                                         | akgulian.com                                  |
| Ackman Dwarfed By Herbalife Spending In Lobbying Battle                                                                     | Business Insider                              |
| Ackman and Herbalife                                                                                                        | FutureOfCapitalism.com                        |
| Ackman outspent by Herbalife in lobbying battle                                                                             | Hedgeworld (subscription)                     |
| Ackman's anti-Herbalife lobbying detailed                                                                                   | MarketWatch (blog)                            |
| Addicted to 'Titanfall'                                                                                                     | CANOE                                         |
| Akron weekly gas update for March 10                                                                                        | Hudson Hub-Times                              |
| All out of dough: Sbarro Pizza files for bankruptcy for the second time in three ...                                        | Daily Mail                                    |
| Amarillo Gas Prices Rise Again                                                                                              | MyHighPlains                                  |
| American Airlines & JetBlue Airways To Terminate Partnership - Quick Facts                                                  | RTT News                                      |
| American Airlines & JetBlue End Agreement                                                                                   | CBS Local                                     |
| American Airlines & JetBlue: Le Divorce                                                                                     | Barron's (blog)                               |
+-----------------------------------------------------------------------------------------------------------------------------+-----------------------------------------------+
```
**(2.)** Which article names have the word `'bitcoin'` in it?                        
Select all the columns.
```sql
 SELECT * FROM news
 WHERE title LIKE '%bitcoin%';
```
### 🟩Output
```sql
|   id | title                                                                   | publisher             | category   |     timestamp | url                                                                                                                                                              |
|------|-------------------------------------------------------------------------|-----------------------|------------|---------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  199 | Bitcoin Exchange Mt. Gox Seeks US Bankruptcy Relief                     | Law360 (subscription) | b          | 1394474320964 | http://www.law360.com/articles/516804/bitcoin-exchange-mt-gox-seeks-us-bankruptcy-relief                                                                         |
|  201 | Bitcoin exchange Mt. Gox files for US bankruptcy protection             | The Globe and Mail    | b          | 1394474321662 | http://www.theglobeandmail.com/report-on-business/international-business/us-business/bitcoin-exchange-mt-gox-files-for-us-bankruptcy-protection/article17392957/ |
|  202 | Hackers Claim Mt. Gox CEO Mark Karpeles Held 'Stolen' Customer Bitcoins | Design & Trend        | b          | 1394474321847 | http://www.designntrend.com/articles/11510/20140310/hackers-strike-again-claiming-mt-gox-ceo-mark-karpeles-held-customer-bitcoins.htm                            |
|  205 | Report: Mt. Gox CEO Holding 'Stolen' Bitcoins                           | PC Magazine           | b          | 1394474322360 | http://www.pcmag.com/article2/0,2817,2454756,00.asp                                                                                                              |
|  209 | Mt. Gox Chief Stole 100000 Bitcoins, Hackers Claim                      | InformationWeek       | b          | 1394474323133 | http://www.informationweek.com/security/attacks-and-breaches/mt-gox-chief-stole-100000-bitcoins-hackers-claim/d/d-id/1114197?_mc=RSS_IWK_EDT                     |
|  213 | Anonymous hackers claim MtGox still has 'stolen' Bitcoins               | SC Magazine UK        | b          | 1394474323797 | http://www.scmagazineuk.com/anonymous-hackers-claim-mtgox-still-has-stolen-bitcoins/article/337507/                                                              |
```
**(3.)** The `category` column contains the article category:              
`'b'` stands for Business                        
`'t'` stands for Technology                                
What are the 20 business articles published most recently?                 
Select all the columns.



























































