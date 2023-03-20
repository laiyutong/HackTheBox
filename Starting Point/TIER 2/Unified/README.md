<h1>Unified</h1>

<h2>CONNECT</h2>
Connect to Starting Point VPN before starting the machine<br>
Using <code>openvpn</code> to operate the file of <code>download vpn</code> in kali.

<h2>TASK</h2>

<h3>TASK 1</h3>
Q：Which are the first four open ports?<br>
A：<code>22,6789,8080,8443</code><br><br>

<h3>TASK 2</h3>
Q：What is the title of the software that is running running on port 8443?<br>
A：<code>UniFi Network</code><br>

<h3>TASK 3</h3>
Q：What is the version of the software that is running?<br>
A：<code>6.4.54</code><br>

<h3>TASK 4</h3>
Q：What is the CVE for the identified vulnerability?<br>
A：<code>CVE-2021-44228</code><br>
FYI：<a href="https://www.sprocketsecurity.com/resources/another-log4j-on-the-fire-unifi">Unified 6.4.54 exploit</a>

<h3>TASK 5</h3>
Q：What protocol does JNDI leverage in the injection?<br>
A：<code>ldap</code><br>
FYI：What is <a href="https://en.wikipedia.org/wiki/Java_Naming_and_Directory_Interface">JNDI</a>？
<img src="https://i.imgur.com/zeayALw.png" alt="JNDI arch" width="40%">

<h3>TASK 6</h3>
Q：What tool do we use to intercept the traffic, indicating the attack was successful?<br>
A：<code>tcpdump</code>

<h3>TASK 7</h3>
Q：What port do we need to inspect intercepted traffic for?<br>
A：<code>389</code><br>

<h3>TASK 8</h3>
Q：What port is the MongoDB service running on?<br>
A：<code>27117</code>

<h3>TASK 9</h3>
Q：What is the default database name for UniFi applications?<br>
A：<code>ace</code><br>

<h3>TASK 10</h3>
Q：What is the function we use to enumerate users within the database in MongoDB?<br>
A：<code>db.admin.find()</code><br>

<h3>TASK 11</h3>
Q：What is the function we use to update users within the database in MongoDB?<br>
A：<code>db.admin.update()</code>

<h3>TASK 12</h3>
Q：What is the password for the root user?<br>
A：<code>NotACrackablePassword4U2022</code>


<h2>SUBMIT FLAG</h2>
22, 6789, 8080, 8443 ports are all open.<br>
<img src="https://github.com/laiyutong/HackTheBox/blob/main/Starting%20Point/TIER%202/Unified/Unified/nmap1.png" alt="nmap1" width="60%">

Open the webpage and go to <target_ip>:<code>8080</code>, you will find that the page automatically jumps to <code>8443</code> port
Click to accept the risk, you will enter the <code>Unifi</code> Network page.<br>
<img src="https://github.com/laiyutong/HackTheBox/blob/main/Starting%20Point/TIER%202/Unified/Unified/nmap2.png" alt="nmap2" width="60%">


<img src="https://github.com/laiyutong/HackTheBox/blob/main/Starting%20Point/TIER%202/Unified/Unified/webredirect.png" alt="webredirect" width="60%">


<img src="https://github.com/laiyutong/HackTheBox/blob/main/Starting%20Point/TIER%202/Unified/Unified/webwarning.png" alt="webwarning" width="60%">

Where there is an account and password to enter, try to log in with SQLi but fail.<br>
<img src="https://github.com/laiyutong/HackTheBox/blob/main/Starting%20Point/TIER%202/Unified/Unified/loginpage.png" alt="loginpage" width="60%">

After opening <code>BurpSuite</code>, go to <code>proxy</code> and <code>Open browser</code>.<br>
<img src="https://github.com/laiyutong/HackTheBox/blob/main/Starting%20Point/TIER%202/Unified/Unified/BP.png" alt="BP" width="60%">


Go back to BurpSuite and <code>turn on</code> intercept ⇒ intercept in on <br>
(intercept information sent on the web page)<br>
<img src="https://github.com/laiyutong/HackTheBox/blob/main/Starting%20Point/TIER%202/Unified/Unified/intercepton.png" alt="intercepton" width="60%">

Go back to the webpage you just opened, and first enter the account password at will.<br>
<img src="https://github.com/laiyutong/HackTheBox/blob/main/Starting%20Point/TIER%202/Unified/Unified/BPbrowser.png" alt="BPbrowser" width="60%">

Back to BurpSuite to see if there are any vulnerabilities that can be exploited.<br>
<img src="https://github.com/laiyutong/HackTheBox/blob/main/Starting%20Point/TIER%202/Unified/Unified/BP2.png" alt="BP2" width="60%">

As shown in the figure below, we can see <code>{username:, password:, remember:, strict:}</code> 
<img src="https://github.com/laiyutong/HackTheBox/blob/main/Starting%20Point/TIER%202/Unified/Unified/SentToRepeater.png" alt="SentToRepeater" width="60%">
<img src="https://github.com/laiyutong/HackTheBox/blob/main/Starting%20Point/TIER%202/Unified/Unified/Repeater.png" alt="Repeater" width="60%">
<img src="https://github.com/laiyutong/HackTheBox/blob/main/Starting%20Point/TIER%202/Unified/Unified/repeaterinvalid.png" alt="repeaterinvalid" width="60%">
<img src="https://github.com/laiyutong/HackTheBox/blob/main/Starting%20Point/TIER%202/Unified/Unified/repeaterinvalid2.png" alt="repeaterinvalid2" width="60%">
<img src="https://github.com/laiyutong/HackTheBox/blob/main/Starting%20Point/TIER%202/Unified/Unified/Repeater2.png" alt="Repeater2" width="60%">
<img src="https://github.com/laiyutong/HackTheBox/blob/main/Starting%20Point/TIER%202/Unified/Unified/tcpdump.png" alt="tcpdump" width="60%">
<img src="https://github.com/laiyutong/HackTheBox/blob/main/Starting%20Point/TIER%202/Unified/Unified/tcpdump2.png" alt="tcpdump2" width="60%">
<img src="https://github.com/laiyutong/HackTheBox/blob/main/Starting%20Point/TIER%202/Unified/Unified/tcpdump3.png" alt="tcpdump3" width="60%">


PS parameter description
<pre text="class">
<b>a</b>：Select all processes except both session leaders (see getsid(2)) and processes not associated with a terminal.
<b>u userlist</b>：Select by effective user ID (EUID) or name.  This selects the processes whose effective user name or ID is in userlist.The effective user ID describes the user whose file access permissions are used by the process (see geteuid(2)).  Identical to U and --user.
<b>x</b>：Lift the BSD-style "must have a tty" restriction, which is imposed upon the set of all processes when some BSD-style (without "-") options are used or when the ps personality setting is BSD-like.The set of processes selected in this manner is in addition to the set of processes selected by other means.  An alternate description is that this option causes ps to list all processes owned by you (same EUID as ps), or to list all processes when used together with the a option.
</pre>


