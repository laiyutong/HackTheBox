<h1>
Vaccine
</h1>

<h2>CONNECT</h2>
Connect to Starting Point VPN before starting the machine<br>
Using <code>openvpn</code> to operate the file of <code>download vpn</code> in kali.

<h2>TASK</h2>

<h3>TASK 1</h3>
Q：Besides SSH and HTTP, what other service is hosted on this box?<br>
A：<code>ftp</code><br><br>

<h3>TASK 2</h3>
Q：This service can be configured to allow login with any password for specific username.<br>
What is that username?<br>
A：<code>anonymous</code><br><br>

<h3>TASK 3</h3>
Q：What is the name of the file downloaded over this service?<br>
A：<code>backup.zip</code><br><br>

<h3>TASK 4</h3>
Q：What script comes with the John The Ripper toolset and generates a hash from a password protected zip archive in a format to allow for cracking attempts?<br>
A：<code>zip2john</code><br><br>

<h3>TASK 5</h3>
Q：What is the password for the admin user on the website?<br>
A：<code>qwerty789</code><br><br>

<h3>TASK 6</h3>
Q：What option can be passed to sqlmap to try to get command execution via the sql injection?<br>
A：<code>--os-shell</code><br><br>

<h3>TASK 7</h3>
Q：What program can the postgres user run as root using sudo?<br>
A：<code>find</code><br><br>

<h2>SUBMIT FLAG</h2>

<a href="https://www.md5online.org/md5-decrypt.html">MD5 Decryption Online Tool</a><br>
FYI：<a href="https://developer.mozilla.org/en-US/docs/Web/HTTP/CookiesUsing">HTTP cookies</a><br>

<code>nmap -sV target_IP</code><br>
<img src="https://i.imgur.com/VU1AWld.png" alt="nmap" width="60%"><br>
<img src="https://i.imgur.com/e4No62m.png" alt="80port" width="60%"><br>
<code>ftp target_IP</code><br>
<img src="https://i.imgur.com/pJHUB1x.png" alt="ftp" width="60%"><br>
<code>unzip backup.zip</code><br> 
<img src="https://i.imgur.com/AZmHnqk.png" alt="unzip" width="60%"><br>
<code>zip2john backup.zip > backup.txt</code><br>
<img src="https://i.imgur.com/u6CvI2J.png" alt="zip2john" width="60%"><br>
<code>john --show backup.txt</code><br>
<img src="https://i.imgur.com/kHui7GU.png" alt="john" width="60%"><br>
<code>cat backup.txt </code><br>
<img src="https://i.imgur.com/oNnGAjw.png" alt="cat" width="60%"><br>
<img src="" alt="" width="60%"><br>
<img src="" alt="" width="60%"><br>
<img src="" alt="" width="60%"><br>
<img src="" alt="" width="60%"><br>
<img src="" alt="" width="60%"><br>
<img src="" alt="" width="60%"><br>
<img src="" alt="" width="60%">
<img src="" alt="" width="60%">
<img src="" alt="" width="60%">
<img src="" alt="" width="60%">
<img src="" alt="" width="60%">
<img src="" alt="" width="60%">
<img src="" alt="" width="60%">
<img src="" alt="" width="60%">
