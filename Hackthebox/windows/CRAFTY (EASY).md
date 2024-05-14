machine IP : 10.10.11.249
startign with the nmap scan 
![](../../attachments/Pasted%20image%2020240507083146.png)

let's do another namp scan with all ports to see if we can get any info

![](../../attachments/Pasted%20image%2020240507084552.png)
we've found that 25565 port is open let's focus on gathering more info 

add the ip to /etc/hosts to access the ip 
![](../../attachments/Pasted%20image%2020240507083257.png)

![](../../attachments/Pasted%20image%2020240507083404.png)

the above result is the result of wappalyzer extension for the website 
let's explore the website 

![](../../attachments/Pasted%20image%2020240507083459.png)

website dashboard 
every option we click is being redirected to comming soon webpage 
we've have dound another subdomain play.crafty.htb let's do subdomain enum to find any sub domains

![](../../attachments/Pasted%20image%2020240507083543.png)

I haven't found anything intresting in the home page of that website but in the coming soon webpage i've found 
![](../../attachments/Pasted%20image%2020240507083832.png)

![](../../attachments/Pasted%20image%2020240507084653.png)

the abpve result is a gobsuter scan result we haven't found anything intresting let's try some directories since we've found some info in comments 
![](../../attachments/Pasted%20image%2020240507085116.png)

Intresting , we've got 403 error saying we don't have access to go that directory

when i searched about port 25565 i got the result saying it's minecraft default port
![](../../attachments/Pasted%20image%2020240507085321.png)

since we got a port let's connect to multiplayer with the machine ip and port number and see what happens

from the nmap scan result i searched for Minecraft vulnerabilities of that version and i found this
![](../../attachments/Pasted%20image%2020240507092437.png)

![](../../attachments/Pasted%20image%2020240507095552.png)

![](../../attachments/Pasted%20image%2020240507103801.png)

![](../../attachments/Pasted%20image%2020240507104237.png)

