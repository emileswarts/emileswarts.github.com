---
layout: post
title: 'Mysql command line automatic login'

---


When connecting to mysql on a few different hosts it can save you time, by saving your mysql details 
in a file that will be used for login.

Create a file like 
<pre> vi ~/mysql_server1.txt </pre>

Insert the following:
 
<pre>[client]
host="server1"
user="username"
password="password"
database="database" </pre> 

In the terminal run the following to use the contents of the file for login:
<pre>mysql --defaults-file="~/mysql_server1.txt" </pre>

then you could even create a bash alias in ~/.bash_aliases

<pre>alias mysqlserver1='mysql --defaults-file="~/mysql_server1.txt"' </pre>
<br />

Now all you need to run at the terminal is: 
<pre>mysqlserver1 </pre>
