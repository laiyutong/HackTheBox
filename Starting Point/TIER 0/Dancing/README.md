<h1>Dancing</h1>

<h2>CONNECT</h2>
Connect to Starting Point VPN before starting the machine<br>
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
<img src="https://github.com/laiyutong/HackTheBox/blob/main/Starting%20Point/TIER%200/Dancing/Dancing/nmap.png" alt="nmap" width="60%">

<h3>TASK 4</h3>
Q：What is the 'flag' or 'switch' we can use with the SMB tool to 'list' the contents of the share?<br>
A：<code>-L</code><br>

<h3>TASK 5</h3>
Q：How many shares are there on Dancing?<br>
A：<code>4</code>
<img src="https://github.com/laiyutong/HackTheBox/blob/main/Starting%20Point/TIER%200/Dancing/Dancing/smbclient.png" alt="smbclient" width="60%">

<h3>TASK 6</h3>
Q：What is the name of the share we are able to access in the end with a blank password?<br>
A：<code>Workshares</code>


<h3>TASK 7</h3>
Q：What is the command we can use within the SMB shell to download the files we find?<br>
A：<code>get</code>


<h2>SUBMIT FLAG</h2>
Trying to connect each share and it can be noticed only WorkShares is connected without providing any password.<br>
command：<code>smbclient //&lt;hostname&gt;/&lt;sharename&gt; -U &lt;username&gt;</code><br>
(<a href="https://web.mit.edu/rhel-doc/5/RHEL-5-manual/Deployment_Guide-en-US/s1-samba-connect-share.html">Connecting to a Samba Share</a>)
<img src="https://github.com/laiyutong/HackTheBox/blob/main/Starting%20Point/TIER%200/Dancing/Dancing/connect.png" alt="connect" width="60%">
<code>flag.txt</code> is found in <code>James.P</code> directory.<br>
<img src="https://github.com/laiyutong/HackTheBox/blob/main/Starting%20Point/TIER%200/Dancing/Dancing/ls.png" alt="ls" width="60%">
Now use <code>get</code> command to download the flag.txt file and you can get the flag！<br>
<img src="https://github.com/laiyutong/HackTheBox/blob/main/Starting%20Point/TIER%200/Dancing/Dancing/get.png" alt="get" width="60%">
