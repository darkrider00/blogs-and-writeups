Starting with a nmap scan 

![](../attachments/1%201.png)

![](../attachments/2%201.png)


we found that Ftp anonymous login is allowed so let's login with ftp

![](../attachments/3%201.png)

we've got some files in ftp
let's try to read those files 

![](../attachments/4%201.png)

![](../attachments/5%201.png)

since port 80 is open let's open our ip in web browser too 

![](../attachments/6%201.png)

meanwhile let's run a gobuster scan to find the directories

![](../attachments/7%201.png)

the files contains same things like ftp 

let's us put our reverse shell  file in FTP and access that in browser to get shell access

![](../attachments/8%201.png)

![](../attachments/10%201.png)

![](../attachments/9%201.png)
We've got a shell here

let's explore the shell

![](../attachments/11%201.png)

![](../attachments/12.png)

we got a txt file here

![](../attachments/13%201.png)

We can’t get in Lennie’s directory so we need to find a way onto their account. When we listed the files earlier there was a directory called “incidents”, let’s see what’s there.

This file might contain something we need. Let’s copy it to the /files/ftp directory so we can access it and check it out in Wireshark. We’ll use the following command to do this:

![](../attachments/15%201.png)

![](../attachments/Pasted%20image%2020240805210325.png)

If we right-click on a packet and select Follow > TCP Stream, we can observe some actions being performed on the target machine in streams two and seven. In stream seven, sudo commands are being entered as the user `www-data`, along with an incorrect password. Let's try using this password for the user Lennie.

![](../attachments/16%201.png)

![](../attachments/17%201.png)

yay! now we logged into use lennie

![](../attachments/18%201.png)

The output file is created by root! This means that root is running an automated task that runs the planner.sh script every minute. Now we can edit the print.sh script to get us a root shell instead of creating an output file.

and we got root access 

![](../attachments/19%201.png)

![](../attachments/20.png)