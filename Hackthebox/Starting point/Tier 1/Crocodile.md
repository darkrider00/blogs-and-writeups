
What Nmap scanning switch employs the use of default scripts during a scan?
Ans: -sC

![](../../../attachments/Pasted%20image%2020240531124729.png)

What service version is found to be running on port 21?
Ans: vsftpd 3.0.3

What FTP code is returned to us for the "Anonymous FTP login allowed" message?
Ans: 230

After connecting to the FTP server using the ftp client, what username do we provide when prompted to log in anonymously?
Ans: anonymous

After connecting to the FTP server anonymously, what command can we use to download the files we find on the FTP server?
![](../../../attachments/Pasted%20image%2020240531125348.png)

we can use get command

What is one of the higher-privilege sounding usernames in 'allowed.userlist' that we download from the FTP server?

![](../../../attachments/Pasted%20image%2020240531125707.png)
Ans: Admin

What version of Apache HTTP Server is running on the target host?
from the nmap scan
Apache httpd 2.4.41

What switch can we use with Gobuster to specify we are looking for specific filetypes?
Ans:-x

Which PHP file can we identify with directory brute force that will provide the opportunity to authenticate to the web service?

![](../../../attachments/Pasted%20image%2020240531130728.png)
we have got login.php let's navigate to login.php in website



![](../../../attachments/Pasted%20image%2020240531131114.png)
let's login with our details

![](../../../attachments/Pasted%20image%2020240531131034.png)

we've got our flag 
Submit root flag
c7110277ac44d*********************