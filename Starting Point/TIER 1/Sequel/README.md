<h1>Sequel</h1>

<h2>CONNECT</h2>
Connect to Starting Point VPN before starting the machine<br>
Using <code>openvpn</code> to operate the file of <code>download vpn</code> in kali.

<h2>TASK</h2>

<h3>TASK 1</h3>
Q：What does the acronym SQL stand for?<br>
A：<code>Structured Query Language</code><br>

<h3>TASK 2</h3>
Q：During our scan, which port running mysql do we find?<br>
A：<code>3306</code><br>

<h3>TASK 3</h3>
Q：What community-developed MySQL version is the target running?<br>
A：<code>MariaDB</code><br>

<h3>TASK 4</h3>
Q：What switch do we need to use in order to specify a login username for the MySQL service?<br>
A：<code>-u</code><br>

<h3>TASK 5</h3>
Q：Which username allows us to log into MariaDB without providing a password?<br>
A：<code>root</code>

<h3>TASK 6</h3>
Q：What symbol can we use to specify within the query that we want to display everything inside a table?<br>
A：<code>*</code>

<h3>TASK 7</h3>
Q：What symbol do we need to end each query with?<br>
A：<code>；</code>

<h2>SUBMIT FLAG</h2>
<img src="https://github.com/laiyutong/HackTheBox/blob/main/Starting%20Point/TIER%201/Sequel/Sequel/nmap.png" alt="nmap" width="60%">

<code>mysql -h <target_ip> -u root</code><br>
Login as root<br>
<img src="https://github.com/laiyutong/HackTheBox/blob/main/Starting%20Point/TIER%201/Sequel/Sequel/mysqllogin.png" alt="mysqllogin" width="60%"><br>
  
<code>select version();</code><br>
Check database version<br>
<img src="https://github.com/laiyutong/HackTheBox/blob/main/Starting%20Point/TIER%201/Sequel/Sequel/showversion.png" alt="showversion" width="30%"><br>

<code>show databases;</code><br>
See what databases are available<br>
<img src="https://github.com/laiyutong/HackTheBox/blob/main/Starting%20Point/TIER%201/Sequel/Sequel/showdb.png" alt="showdb" width="30%"><br>

<code>show tables;</code><br>
See what tables are available<br>
<img src="https://github.com/laiyutong/HackTheBox/blob/main/Starting%20Point/TIER%201/Sequel/Sequel/showtables.png" alt="showtables" width="30%"><br>

<code>select * from &lt;tables&gt;;</code><br>
Read the information in the table and you'll see the flag！<br>
<img src="https://github.com/laiyutong/HackTheBox/blob/main/Starting%20Point/TIER%201/Sequel/Sequel/readtable.png" alt="readtable" width="60%"><br>



