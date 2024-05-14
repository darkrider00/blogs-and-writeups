Lab URL :
https://0ac7003b03b289fd80483a4d00050045.web-security-academy.net/

![](../../attachments/Pasted%20image%2020240514185624.png)

This lab objective is to  read /etc/passwd file from the url 
![](../../attachments/Pasted%20image%2020240514185739.png)

![](../../attachments/Pasted%20image%2020240514190029.png)

we can click on view item to get the more details about the product and if we look at the url :
```
https://0ac7003b03b289fd80483a4d00050045.web-security-academy.net/product?productId=1
```
but the parameter should be filename if we want to inject the payload so let's open a image in new tab 
![](../../attachments/Pasted%20image%2020240514190534.png)

if we look at the url now :
```
https://0ac7003b03b289fd80483a4d00050045.web-security-academy.net/image?filename=38.jpg
```
since we have a filename as a parameter we can use ../../../etc/passwd 
but before that let's change the file number and see if can we get a different image 
![](../../attachments/Pasted%20image%2020240514190736.png)

here we changed the filename from 38.jpg to 30.jpg here we can access another files by changing the parameter values in the URL

so now let's try our payload `../../../etc/passwd` to read the password file 
![](../../attachments/Pasted%20image%2020240514191137.png)

we got nothing so there might be some kind of input sanitization here so instead of giving a indirect path to the file let's directly specify `/etc/passed` to get access to the file

![](../../attachments/Pasted%20image%2020240514192015.png)

if we want to view the file we need to intercept this request using burp suite

![](../../attachments/Pasted%20image%2020240514192543.png)

we have our request captured in the burpsuite repeater
let's inject our payload

![](../../attachments/Pasted%20image%2020240514192759.png)

as we can see we are able to view all files that we shouldn't access

for more information refer : https://youtu.be/Wt0gk05MBz0
