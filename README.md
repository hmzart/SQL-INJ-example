# SQL INJECTION
## What is SQL injection

**Author : By Hamza Erten**


SQL injection is a web security vulnerability that allows an attacker to interfere with the queries that an application makes to its database. It generally allows an attacker to view data that they are not normally able to retrieve. This might include data belonging to other users, or any other data that the application itself is able to access. In many cases, an attacker can modify or delete this data, causing persistent changes to the application's content or behavior.

![sql-injection](https://user-images.githubusercontent.com/103367369/164241893-e0250f37-2bd0-4c23-83e4-e1f97d7b085a.svg)

## Types of SQL Injections

1- )
In-band SQLi (Classic)
Error-based SQLi
Union-based SQLi

2 -)
Inferential SQLi (Blind)
Boolean-based SQLi
Time-based SQLi

3-) 
Out-of-band SQLi

# 1) In-band SQLi (Classic)
It is the most common and easy-to-use of SQL Injection attacks. An attacker uses the same communication channel to both launch the attack and collect the results.

**a) Error-based SQLi**


It is a SQL Injection technique based on error messages thrown by the database server to obtain information about the structure of the database. In some cases, error-based SQL injection alone is sufficient for an attacker to enumerate the entire database. Although bugs are very useful during the development phase of a web application, they should be disabled on a live site or logged into a file with limited access instead. Here are a few examples that I found on the Internet for this category.


 *Select * from stores where product_id = blah’ or 1=1-- (after that everything will be ignored by the system dec)*
 
 
 **b) Union-based SQLi**
 
 It is a SQL Injection technique that uses the UNION SQL operator to combine the results of two or more “SELECT” statements into a single result, which is then returned as part of the HTTP response. In this HTTP response, it may contain data that can be used by the attacker. The examples I have found for this category are: 
 
 *Select * from stores where product_id=1 union select 1,database(),user(),4#*
 
 *Select * from stores where id=1’*
 
  # **2) Inferential SQLi (Blind)**
  
  Unlike In-band SQL Injection, Inferential SQL Injection may take longer for an attacker to exploit, but it is just as dangerous as other types of SQL Injection. In an Inferential SQL attack, no data is actually transferred through the web application, and the attacker cannot see the result of the attack (which is why such attacks are often called “blind SQL Injection attacks”). Instead, an attacker can recreate the database structure by sending data, observing the response of the web application and the resulting behavior of the database server.
  
  **a) Boolean-based Blind SQL Injections**
  
  It is an SQL Injection technique based on sending an SQL query to the database and forcing the application to return a different result depending on whether the query returns a TRUE or FALSE result.

Depending on the result, the content in the HTTP response will change or remain the same. This allows an attacker to figure out whether the used payload is returning true or false, even if no data has been returned from the database. Since an attacker will need to enumerate a database by character, this attack is usually slow (especially in large databases).
  
  *www.shop.com/item.php?id=34 and 1=2*
 
 
 **b) Time-based Blind SQL Injections**
 
An attacker sends an SQL query to the database, allowing it to wait (for a period of seconds) for the database to respond. The attacker can see the time it takes for the database to respond, whether a query is true or false. Depending on the result, an HTTP response will be generated instantly or after a waiting period. Without relying on the data in the database, the attacker can calculate whether the message they are using returns true or false.

*http://wwwshop.local/item.php?id=34 and if(1=1, sleep(10), false)*

 # 3) Out-of-band SQLi
 
 This technique is not very common, since it depends mostly on some of the features that are enabled on the database server used by the web application. In this attack, it occurs when the attacker is unable to use the same channel to launch the attack and collect the results.

Out-of-band techniques provide an attacker with an alternative to inferential time-based techniques, especially when server responses are not very stable (which makes an inferential time-based attack unreliable).

Out-of-band SQLi techniques rely on the database server's ability to make DNS or HTTP requests to provide data to an attacker.

# Preventing and reducing SQL Injection attacks

In addition to preventing QLI attacks from happening, there are several effective ways to protect against them.

The first step is to check the user entries. If the user enters any SQL phrase, it should be mandatory to check, evaluate this entry by the system.

Another solution is to commonly use a web application firewall (WAF) to filter SQL Injection or other online threats. Modern web application firewalls are also often integrated with other security solutions.


 ## SQL(i) Examples;
 
# SQL Injection Based on 1=1 is Always True
For example, there is a user named user on your site. And if you don't know the password, you can log in with the parameter 1 =1 using Or.
UserID
![sql_injection](https://user-images.githubusercontent.com/103367369/164253413-5608a55b-747e-40a0-b2b0-962638a5d019.gif)

## -----
# New senario 
If you enter the username as user'#, you can login without even knowing what the password is.

![pwpwpwp](https://user-images.githubusercontent.com/103367369/164258300-b910cff1-9493-4b3e-ab01-131a6df8f43f.PNG)







