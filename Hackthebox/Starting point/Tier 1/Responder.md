
![](../../../attachments/Pasted%20image%2020240531132119.png)

nmap scan 

![](../../../attachments/Pasted%20image%2020240531132142.png)

unika.htb

Which scripting language is being used on the server to generate webpages?

![](../../../attachments/Pasted%20image%2020240531132806.png)
PHP

What is the name of the URL parameter which is used to load different language versions of the webpage?

Ans: page

Which of the following values for the `page` parameter would be an example of exploiting a Local File Include (LFI) vulnerability: "french.html", "//10.10.14.6/somefile", "../../../../../../../../windows/system32/drivers/etc/hosts", "minikatz.exe"

url : http://unika.htb/index.php?page=/../../../../../../../windows/system32/drivers/etc/hosts

![](../../../attachments/Pasted%20image%2020240531133013.png)



Which of the following values for the `page` parameter would be an example of exploiting a Remote File Include (RFI) vulnerability: "french.html", "//10.10.14.6/somefile", "../../../../../../../../windows/system32/drivers/etc/hosts", "minikatz.exe"



What does NTLM stand for?

New Technology Lan Manager

Which flag do we use in the Responder utility to specify the network interface?

![](../../../attachments/Pasted%20image%2020240531133759.png)

let's clone this repo

-I is used to specify the flag

There are several tools that take a NetNTLMv2 challenge/response and try millions of passwords to see if any of them generate the same response. One such tool is often referred to as `john`, but the full name is what?.

John the ripper

What is the password for the administrator user?

using JTR tool : badminton 

We'll use a Windows service (i.e. running on the box) to remotely access the Responder machine using the password we recovered. What port TCP does it listen on?

![](../../../attachments/Pasted%20image%2020240531135611.png)

5985


![](../../../attachments/Pasted%20image%2020240531135923.png)

we got our flag 
Submit root flag