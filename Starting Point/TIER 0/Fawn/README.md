<h1>Fawn</h1>

<h2>CONNECT</h2>
Connect to Starting Point VPN before starting the machine<br>
<img src="https://github.com/laiyutong/HackTheBox/blob/main/Starting%20Point/TIER%200/Fawn/Fawn/download.png" alt="download" width="30%">
Using <code>openvpn</code> to operate the file of <code>download vpn</code> in kali.
<img src="https://github.com/laiyutong/HackTheBox/blob/main/Starting%20Point/TIER%200/Fawn/Fawn/openvpn.png" alt="openvpn" width="60%">

<h2>TASK</h2>

<h3>TASK 1</h3>
Q：What does the 3-letter acronym FTP stand for?<br>
A：<code>File Transfer Protocol</code>

<h3>TASK 2</h3>
Q：Which port does the FTP service listen on usually?<br>
A：<code>21</code><br>
<img src="https://i.imgur.com/ODy4l1R.png" alt="port" width="60%">

<h3>TASK 3</h3>
Q：What acronym is used for the secure version of FTP?<br>
A：<code>SFTP</code><br>
<a href="https://www.ssh.com/academy/ssh/sftp-ssh-file-transfer-protocol">SSH File Transfer Protocol</a>

<h3>TASK 4</h3>
Q：What is the command we can use to send an ICMP echo request to test our connection to the target?<br>
A：<code>ping</code><br>
<a href="Ping – Manually create and send ICMP/IP packets">Ping - Manually create and send ICMP/IP packets</a>

<h3>TASK 5</h3>
Q：From your scans, what version is FTP running on the target?<br>
A：<code>vsftpd 3.0.3</code>
<img src="https://github.com/laiyutong/HackTheBox/blob/main/Starting%20Point/TIER%200/Fawn/Fawn/nmap.png" alt="nmap" width="60%">

<h3>TASK 6</h3>
Q：From your scans, what OS type is running on the target?<br>
A：<code>Unix</code>
<img src="https://github.com/laiyutong/HackTheBox/blob/main/Starting%20Point/TIER%200/Fawn/Fawn/nmap.png" alt="nmap" width="60%">

<h3>TASK 7</h3>
Q：What is the command we need to run in order to display the 'ftp' client help menu?<br>
A：<code>ftp -h</code>

<h3>TASK 8</h3>
Q：What is username that is used over FTP when you want to log in without having an account?<br>
A：<code>anonymous</code><br>
<a href="https://www.geeksforgeeks.org/what-is-anonymous-ftp-file-transfer-protocol/">Anonymous FTP</a>

<h3>TASK 9</h3>
Q：What is the response code we get for the FTP message 'Login successful'?<br>
A：<code>230</code><br>
<a href="https://en.wikipedia.org/wiki/List_of_FTP_server_return_codes">List of FTP server return codes</a>

<h3>TASK 10</h3>
Q：There are a couple of commands we can use to list the files and directories available on the FTP server.<br>
One is dir. What is the other that is a common way to list files on a Linux system.<br>
A：<code>ls</code>

<h3>TASK 11</h3>
Q：What is the command used to download the file we found on the FTP server?<br>
A：<code>get</code>

<h2>SUBMIT FLAG</h2>
Using name：<code>anonymous</code> and password：<code>NULL</code> to login.
<img src="https://github.com/laiyutong/HackTheBox/blob/main/Starting%20Point/Fawn/Fawn/FTP.png" alt="FTP" width="40%">
You can try <code>ls</code> to see if anything exists.
Apparently, there exists a <code>flag.txt</code> as shown below,<br>
we need to do is find a way to get the content of the flag.txt.
<img src="https://github.com/laiyutong/HackTheBox/blob/main/Starting%20Point/TIER%200/Fawn/Fawn/ls.png" alt="ls" width="60%">
You can use <code>help</code> to check what command can be used.
<img src="https://github.com/laiyutong/HackTheBox/blob/main/Starting%20Point/TIER%200/Fawn/Fawn/help.png" alt="help" width="60%">
Ultimately, you can get the flag by using <code>get</code> command！
<img src="https://github.com/laiyutong/HackTheBox/blob/main/Starting%20Point/TIER%200/Fawn/Fawn/get.png" alt="get" width="60%">
