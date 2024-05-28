
![](../../attachments/Pasted%20image%2020240528145236.png)

From the lab description we know that There is SQL vulnerability in product category filter. To solve the lab we need to display the database version string 

Here the database is My SQL ,
Let's head over to SQL cheat sheet for payloads refer to sql sheet for here 

![](../../attachments/Pasted%20image%2020240528150258.png)

here are the available list of payloads we can use for different types of databases

Let's access the lab 
![](../../attachments/Pasted%20image%2020240528151802.png)

the same thing we have here it will refine your search based on the category you select for detail walkthrough refer to [SQL injection attack, querying the database type and version on Oracle](SQL%20injection%20attack,%20querying%20the%20database%20type%20and%20version%20on%20Oracle.md)

so let's generate the payload here 

`'UNION SELECT @@version, NULL#`

let's inject out payload in request we captured
![](../../attachments/Pasted%20image%2020240528152458.png)

if we inject order by 3 we get internal sever error so number of columns is 2 itself and to check weather both columns are same data type or not to fulfill the conditions of union attack 
`UNION SELECT 'a','a'#`

![](../../attachments/Pasted%20image%2020240528154319.png)

since they are same data type we can inject our payload from SQL cheat sheet

![](../../attachments/Pasted%20image%2020240528154551.png)

![](../../attachments/Pasted%20image%2020240528154631.png)



