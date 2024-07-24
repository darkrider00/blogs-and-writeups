
![](../attachments/Pasted%20image%2020240724111400.png)


Let's start with a nmap scan

we have port 80 open so let's access this in our browser

![](../attachments/Pasted%20image%2020240724111718.png)

we got a terminal here

![](../attachments/Pasted%20image%2020240724111813.png)

we got some commands here 

![](../attachments/Pasted%20image%2020240724112328.png)

when i visited to robots.txt to gather more information i got 2 files one is a dictionary file and another one is a key which is our first answer 

so get those files 

![](../attachments/Pasted%20image%2020240724112531.png)

we got our first key 
![](../attachments/Pasted%20image%2020240724112655.png)

in the hint of the 2nd key they mentioned abput the worldlist 
![](../attachments/Pasted%20image%2020240724112754.png)
Upon brute forcing the directories using the dictionary file we found, some interesting files were found

![](../attachments/Pasted%20image%2020240724113206.png)

we got some hits here and the interesting thing we find  here is license let's explore it 

![](../attachments/Pasted%20image%2020240724113349.png)

![](../attachments/Pasted%20image%2020240724113528.png)

we got some encoded value let's decode it using cyberchef 
![](../attachments/Pasted%20image%2020240724113732.png)

when we decode we got something that looks like username ans password 

in our gobuster scan we got some other hits too
![](../attachments/Pasted%20image%2020240724113832.png)

let's check them 

![](../attachments/Pasted%20image%2020240724113941.png)

there is nothing in this page 

since we have a username and password let's go to login page 

![](../attachments/Pasted%20image%2020240724114137.png)

it's a wordpress login page let's login 
![](../attachments/Pasted%20image%2020240724114320.png)

we got a wordpress admin login page

![](../attachments/Pasted%20image%2020240724114543.png)

here in the appearance section we have something called editor where we can edit and update the files directly so we can upload a payload and gain reverse shell access

[reverse shell](https://github.com/pentestmonkey/php-reverse-shell/blob/master/php-reverse-shell.php) can be added in the file and upload it and gain a reverse shell

![](../attachments/Pasted%20image%2020240724115032.png)

change the ip and port according to ur specifications and update the header.php file to gain reverse shell access

![](../attachments/Pasted%20image%2020240724120529.png)

when we open header.php in new tab we got our reverse shell access

![](../attachments/Pasted%20image%2020240724120558.png)

using `python -cimport pty;pty.spawn("/bin/bash");` we can get a stable shell 

![](../attachments/Pasted%20image%2020240724120938.png)

![](../attachments/Pasted%20image%2020240724121036.png)
we are getting permission denied it seems we need to be a user 'robot' to be able to read those files

we have another file called password since the name of the file contains md5 i think its a md5 hash

![](../attachments/Pasted%20image%2020240724121315.png)

we got some hash value for password so let's match it using https://crackstation.net/ 

![](../attachments/Pasted%20image%2020240724121423.png)

we got a match for the password we can now login to the user robot

![](../attachments/Pasted%20image%2020240724121519.png)

and we are logged in to the user as robot 

![](../attachments/Pasted%20image%2020240724121635.png)
we got our second key !!

now we need to be root to get the 3rd key 

![](../attachments/Pasted%20image%2020240724121819.png)
i think we can't escalate privileges with robot's password

let's try another way 

Privilege can be escalate by running nmap --interactive and !sh aftrwards

```
Privilege escalation via `nmap --interactive` involves leveraging a feature from an older version of nmap that allowed users to drop into a shell. This feature is removed in recent versions due to its security implications. Here's how it worked:

### Using `nmap --interactive`

1. **Interactive Mode**: Older versions of `nmap` (prior to 5.21) had an interactive mode which could be accessed using the `--interactive` flag. In this mode, users could issue commands directly to the nmap interpreter.
    
2. **Gaining Shell Access**: By entering `!sh` in the interactive mode, the user could escape to a shell. This is how it worked:
    
    bash
    
    Copy code
    
    `nmap --interactive`
    
    Once in interactive mode, typing `!sh` would open a new shell with the same privileges as the nmap process. If `nmap` was running with elevated privileges (e.g., as root), the new shell would also have those privileges.
    
3. **Exploiting Privileges**: If the user has managed to run `nmap` with higher privileges, this shell would grant them those same privileges, effectively escalating their own privileges.
```

![](../attachments/Pasted%20image%2020240724122121.png)

 and we got our root access now we can read our last key 
 
![](../attachments/Pasted%20image%2020240724122409.png)

we got our all keys and completed our room 

![](../attachments/Pasted%20image%2020240724122511.png)