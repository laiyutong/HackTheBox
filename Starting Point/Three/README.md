<h1>Three</h1>

<h2>CONNECT</h2>
Connect to Starting Point VPN before starting the machine<br>
<img src="https://github.com/laiyutong/HackTheBox/blob/main/Starting%20Point/Fawn/Fawn/download.png" alt="download" width="30%">
Using <code>openvpn</code> to operate the file of <code>download vpn</code> in kali.

<h2>TASK</h2>

<h3>TASK 1</h3>
Q：How many TCP ports are open?<br>
A：<code>-sC</code><br>
<img src="https://github.com/laiyutong/HackTheBox/blob/main/Starting%20Point/Crocodile/crocodile/-sC.png" alt="-sC" width="60%">

<h3>TASK 2</h3>
Q：What is the domain of the email address provided in the "Contact" section of the website?<br>
A：<code>vsftpd 3.0.3</code><br>
<img src="https://github.com/laiyutong/HackTheBox/blob/main/Starting%20Point/Crocodile/crocodile/version.png" alt="version" width="60%">

<h3>TASK 3</h3>
Q：In the absence of a DNS server, which Linux file can we use to resolve hostnames to IP addresses in order to be able to access the websites that point to those hostnames?<br>
A：<code>230</code><br>
<img src="https://github.com/laiyutong/HackTheBox/blob/main/Starting%20Point/Crocodile/crocodile/statuscode.png" alt="statuscode" width="60%">
By the way, <a href="https://nmap.org/nsedoc/scripts/">NSE Scripts</a> is useful to find out how to use or what parameters are available.<br>
<code>ftp-anon</code> mentioned in the picture, can also be found in <a href="https://nmap.org/nsedoc/scripts/">NSE Scripts</a>.<br>
<code>ftp-anon：Checks if an FTP server allows anonymous logins.</code>

<h3>TASK 4</h3>
Q：Which sub-domain is discovered during further enumeration?<br>
A：<code>get</code><br>

<h3>TASK 5</h3>
Q：Which service is running on the discovered sub-domain?<br>
A：<code>admin</code>

<h3>TASK 6</h3>
Q：Which command line utility can be used to interact with the service running on the discovered sub-domain?<br>
A：<code>2.4.41</code>
<img src="https://github.com/laiyutong/HackTheBox/blob/main/Starting%20Point/Crocodile/crocodile/apache.png" alt="apache" width="60%">

<h3>TASK 7</h3>
Q：Which command is used to set up the AWS CLI installation?<br>
A：<code>wappalyzer</code>

<h3>TASK 8</h3>
Q：What is the command used by the above utility to list all of the S3 buckets?<br>
A：<code>-x</code><br>
Using <code>gobuster dir -h</code> to get more info about command.<br>
<img src="https://github.com/laiyutong/HackTheBox/blob/main/Starting%20Point/Crocodile/crocodile/filetype.png" alt="filetype" width="60%">

<h3>TASK 9</h3>
Q：What is the command used by the above utility to list all of the S3 buckets?<br>
A：<code>login.php</code>
<img src="https://github.com/laiyutong/HackTheBox/blob/main/Starting%20Point/Crocodile/crocodile/dirsearch.png" alt="dirsearch" width="60%">

<h2>SUBMIT FLAG</h2>
