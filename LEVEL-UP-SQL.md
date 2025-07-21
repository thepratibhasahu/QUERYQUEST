# RPA Fraud Detection

Reputable Product Agency (RPA) has started receiving complaints from their credit card processor about fraudulent transactions. Help your finance department identify potentially risky transactions before they finish processing.

This dataset contains a single table, `transaction_data`.

→ Table diagram

<img width="644" height="397" alt="image" src="https://github.com/user-attachments/assets/92588a62-72d4-46d8-bb0e-c5f04d8becff" />

**(1.)** Start by getting a feel for the `transaction_data` table:                         
What are the column names?
```SQL
SELECT *
FROM transaction_data
LIMIT 10;
```
### 🟩Output
```SQL
id   full_name        	        email                                zip    ip_address
1    Menard Peniman           	mpeniman0@yahoo.co.jp                92132  223.107.70.220
2    Paulita Boome            	pboome1@over-blog.com                94154  164.183.91.223
3    Barnabe Unthank          	bunthank2@blinklist.com              65110  167.248.251.58
4    Boigie Hughes            	bhughes3@simplemachines.org          98104  219.28.158.36
5    Trudi Rawet              	trawet4@multiply.com                 91199  76.97.141.59
6    Elset Paviour            	epaviour5@google.com                 84105  93.210.178.222
7    Cammi Colthard           	ccolthard6@newyorker.com             75049  126.17.241.252
8    Kristal Bleasdale        	kbleasdale7@ca.gov                   79977  192.94.201.227
9    Donovan Worsalls         	dworsalls8@wikimedia.org             20078  101.219.105.228
10   Lynna Grindley           	lgrindley9@studiopress.com           72204  149.164.116.199
```
**(2.)** The finance department noted that some of the fraudulent transactions were recorded as coming from Smokey Bear’s zip code (20252).                
You agree this is suspicious, it’s unlikely that the fire prevention mascot is using Reputable Company’s services.          
Find the `full_names` and `emails` of the transactions listing 20252 as the zip code.
```sql
SELECT full_name, email, zip
FROM transaction_data
WHERE zip = 20252;
```
