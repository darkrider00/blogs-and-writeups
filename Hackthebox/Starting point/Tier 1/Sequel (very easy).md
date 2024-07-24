TASK 1

During our scan, which port do we find serving MySQL?

![](../../../attachments/Pasted%20image%2020240531104612.png)

on port 3306 mysql is running 


TASK 2

What community-developed MySQL version is the target running?
Ans: Maria DB

TASK 3

When using the MySQL command line client, what switch do we need to use in order to specify a login username?

![](../../../attachments/Pasted%20image%2020240531105451.png)

![](../../../attachments/Pasted%20image%2020240531105851.png)

using the mysql manual page now we know that -h is used to connect to a host  and -u used to specify the username

TASK 4

Which username allows us to log into this MariaDB instance without providing a password?
Ans: root

TASK 5

In SQL, what symbol can we use to specify within the query that we want to display everything inside a table?
Ans : *

TASK 6

In SQL, what symbol do we need to end each query with?
Ans: ;

TASK 7

There are three databases in this MySQL instance that are common across all MySQL instances. What is the name of the fourth that's unique to this host?
https://www.mysqltutorial.org/mysql-cheat-sheet/ refer to this for more detailed information

![](../../../attachments/Pasted%20image%2020240531123043.png)

we are in now let's continue
![](../../../attachments/Pasted%20image%2020240531123247.png)

the database unique to this host is htb let's use htb 
![](../../../attachments/Pasted%20image%2020240531123547.png)

Submit root flag
Ans: 7b4bec00dla39************