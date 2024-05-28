
![](../../attachments/Pasted%20image%2020240528170339.png)

from the lab description 
we know that there is SQL vulnerability in product category filter , to solve the lab we need to perform a union attack that determine number of columns

let's access the lab
The website
![](../../attachments/Pasted%20image%2020240528170956.png)

to display null values we need to use the payload
'+UNION+SELECT+NULL--  if 1 column in ther if 2 colums are there then we need tp use 2 NULLs so on 

![](../../attachments/Pasted%20image%2020240528171412.png)

i've started with null value and i got internal server error let's try 2
![](../../attachments/Pasted%20image%2020240528171452.png)

same result let's go for three

![](../../attachments/Pasted%20image%2020240528171523.png)

and the error disappeared so we determined the number of columns are three and we solved the lab 

![](../../attachments/Pasted%20image%2020240528171607.png)