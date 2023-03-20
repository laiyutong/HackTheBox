<h1>Crocodile</h1>

<h2>CONNECT</h2>
Connect to Starting Point VPN before starting the machine<br>
Using <code>openvpn</code> to operate the file of <code>download vpn</code> in kali.

<h2>TASK</h2>

<h3>TASK 1</h3>
Q：What nmap scanning switch employs the use of default scripts during a scan?<br>
A：<code>-sC</code><br>
<img src="https://github.com/laiyutong/HackTheBox/blob/main/Starting%20Point/TIER%201/Crocodile/crocodile/-sC.png" alt="-sC" width="60%">

<h3>TASK 2</h3>
Q：During our scan, which port running mysql do we find?What service version is found to be running on port 21?<br>
A：<code>vsftpd 3.0.3</code><br>
<img src="https://github.com/laiyutong/HackTheBox/blob/main/Starting%20Point/TIER%201/Crocodile/crocodile/version.png" alt="version" width="60%">

<h3>TASK 3</h3>
Q：What FTP code is returned to us for the "Anonymous FTP login allowed" message?<br>
A：<code>230</code><br>
<img src="https://github.com/laiyutong/HackTheBox/blob/main/Starting%20Point/Crocodile/crocodile/statuscode.png" alt="statuscode" width="60%">
By the way, <a href="https://nmap.org/nsedoc/scripts/">NSE Scripts</a> is useful to find out how to use or what parameters are available.<br>
<code>ftp-anon</code> mentioned in the picture, can also be found in <a href="https://nmap.org/nsedoc/scripts/">NSE Scripts</a>.<br>
<code>ftp-anon：Checks if an FTP server allows anonymous logins.</code>

<h3>TASK 4</h3>
Q：What command can we use to download the files we find on the FTP server?<br>
A：<code>get</code><br>

<h3>TASK 5</h3>
Q：What is one of the higher-privilege sounding usernames in the list we retrieved?<br>
A：<code>admin</code>

<h3>TASK 6</h3>
Q：What version of Apache HTTP Server is running on the target host?<br>
A：<code>2.4.41</code>
<img src="https://github.com/laiyutong/HackTheBox/blob/main/Starting%20Point/TIER%201/Crocodile/crocodile/apache.png" alt="apache" width="60%">

<h3>TASK 7</h3>
Q：What is the name of a handy web site analysis plug-in we can install in our browser?<br>
A：<code>wappalyzer</code>

<h3>TASK 8</h3>
Q：What switch can we use with gobuster to specify we are looking for specific file types?<br>
A：<code>-x</code><br>
Using <code>gobuster dir -h</code> to get more info about command.<br>
<img src="https://github.com/laiyutong/HackTheBox/blob/main/Starting%20Point/TIER%201/Crocodile/crocodile/filetype.png" alt="filetype" width="60%">

<h3>TASK 9</h3>
Q：What file have we found that can provide us a foothold on the target?<br>
A：<code>login.php</code>
<img src="https://github.com/laiyutong/HackTheBox/blob/main/Starting%20Point/TIER%201/Crocodile/crocodile/dirsearch.png" alt="dirsearch" width="60%">

<h2>SUBMIT FLAG</h2>
Use <code>ftp</code> to connect to the ip of the target machine,<br> 
you can see that there are two files: <code>allowed.userlist</code> and <code>allowed.userlist.passwd</code>
<img src="https://github.com/laiyutong/HackTheBox/blob/main/Starting%20Point/TIER%201/Crocodile/crocodile/getflag1.png" alt="getflag1" width="60%">

After downloading two files with <code>get</code> command,<br> 
open them with <code>cat</code>, and you can see four groups of account numbers and passwords.<br>
<img src="https://github.com/laiyutong/HackTheBox/blob/main/Starting%20Point/TIER%201/Crocodile/crocodile/cat.png" alt="cat" width="30%">

Open the website and enter the IP of the target machine,<br> 
the screen is shown as below, it seems that there is no place to log in.<br>
<img src="https://github.com/laiyutong/HackTheBox/blob/main/Starting%20Point/TIER%201/Crocodile/crocodile/web.png" alt="web" width="60%">

You can use <code>dirsearch</code> or <code>gobuster</code> to blast directories and files of the webpage,<br>
and you can find <code>/login.php</code>.<br>
<img src="https://github.com/laiyutong/HackTheBox/blob/main/Starting%20Point/TIER%201/Crocodile/crocodile/dirsearch.png" alt="dirsearch" width="60%">

Add <code>/login.php</code> after the webpage ip to get the login page.<br>
Since the highest authority is <code>admin</code>, fill in admin and the password.<br>
<img src="https://github.com/laiyutong/HackTheBox/blob/main/Starting%20Point/TIER%201/Crocodile/crocodile/loginphp.png" alt="loginphp" width="60%">

After successful login, you can get the flag!<br>
<img src="https://github.com/laiyutong/HackTheBox/blob/main/Starting%20Point/TIER%201/Crocodile/crocodile/flag.png" alt="flag" width="60%">
