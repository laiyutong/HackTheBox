<h1>Dancing</h1>

<h2>CONNECT</h2>
Connect to Starting Point VPN before starting the machine<br>
<img src="https://github.com/laiyutong/HackTheBox/blob/main/Starting%20Point/Fawn/Fawn/download.png" alt="download" width="30%">
Using <code>openvpn</code> to operate the file of <code>download vpn</code> in kali.

<h2>TASK</h2>

<h3>TASK 1</h3>
Q：What does the 3-letter acronym SMB stand for?<br>
A：<code>Server Message Block</code><br>
<a href="https://nordvpn.com/zh-tw/blog/what-is-smb/">What is the SMB protocol?</a>

<h3>TASK 2</h3>
Q：What port does SMB use to operate at?<br>
A：<code>445</code><br>

<h3>TASK 3</h3>
Q：What is the service name for port 445 that came up in our Nmap scan?<br>
A：<code>microsoft-ds</code><br>
<img src="https://github.com/laiyutong/HackTheBox/blob/main/Starting%20Point/Dancing/Dancing/nmap.png" alt="nmap" width="60%">

<h3>TASK 4</h3>
Q：What is the 'flag' or 'switch' we can use with the SMB tool to 'list' the contents of the share?<br>
A：<code>-l</code><br>

<h3>TASK 5</h3>
Q：How many shares are there on Dancing?<br>
A：<code>4</code>
<img src="https://github.com/laiyutong/HackTheBox/blob/main/Starting%20Point/Dancing/Dancing/smbclient.png" alt="smbclient" width="60%">

<h3>TASK 6</h3>
Q：What is the name of the share we are able to access in the end with a blank password?<br>
A：<code>Workshares</code>


<h3>TASK 7</h3>
Q：What is the command we can use within the SMB shell to download the files we find?<br>
A：<code>get</code>


<h2>SUBMIT FLAG</h2>
Using name：<code>anonymous</code> and password：<code>NULL</code> to login.
<img src="https://github.com/laiyutong/HackTheBox/blob/main/Starting%20Point/Fawn/Fawn/FTP.png" alt="FTP" width="40%">
You can try <code>ls</code> to see if anything exists.
Apparently, there exists a <code>flag.txt</code> as shown below,<br>
we need to do is find a way to get the content of the flag.txt.
<img src="https://github.com/laiyutong/HackTheBox/blob/main/Starting%20Point/Fawn/Fawn/ls.png" alt="ls" width="60%">
You can use <code>help</code> to check what command can be used.
<img src="https://github.com/laiyutong/HackTheBox/blob/main/Starting%20Point/Fawn/Fawn/help.png" alt="help" width="60%">
Ultimately, you can get the flag by using <code>get</code> command！
<img src="https://github.com/laiyutong/HackTheBox/blob/main/Starting%20Point/Fawn/Fawn/get.png" alt="get" width="60%">
