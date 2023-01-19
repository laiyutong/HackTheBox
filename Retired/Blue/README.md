<h1>Blue</h1>

<h2>CONNECT</h2>
Connect to Starting Point VPN before starting the machine<br>
<img src="https://github.com/laiyutong/HackTheBox/blob/main/Starting%20Point/Fawn/Fawn/download.png" alt="download" width="30%">
Using <code>openvpn</code> to operate the file of <code>download vpn</code> in kali.

<h2>SUBMIT FLAG</h2>
<h3>Method 1 - Metasploit</h3>
<code>Nmap</code> find three standard <code>Windows</code> ports in <code>135</code> (RPC), <code>139</code> (NetBios), and <code>445</code> (SMB).<br>
<b>command</b>：<code>nmap -p- -Pn &lt;ip&gt; --min-rate 5000</code><br>
<img src="https://github.com/laiyutong/HackTheBox/blob/main/Retired/Blue/blue/nmap.png" alt="nmap" width="80%">
<code>Nmap</code> has <code>vuln scripts</code> that will check for known vulnerabilities in service.<br>
<b>command</b>：<code>nmap --script=vuln -v -p &lt;port&gt;&lt;ip&gt;</code><br>
<img src="https://github.com/laiyutong/HackTheBox/blob/main/Retired/Blue/blue/vulnnmap.png" alt="vulnnmap" width="80%">
Because the vulnerable script scans out as ms17-010, use msfconsole: search ms17-010.<br>
<b>command</b>：<code>search ms17-010</code><br>
<img src="https://github.com/laiyutong/HackTheBox/blob/main/Retired/Blue/blue/search.png" alt="search" width="80%">
<code>show options</code>：Show module options<br>
<img src="https://github.com/laiyutong/HackTheBox/blob/main/Retired/Blue/blue/showoptions.png" alt="showoptions" width="80%">
<code>set</code> command to set parameters, and finally use <code>run</code> command to start the attack.<br>
<img src="https://github.com/laiyutong/HackTheBox/blob/main/Retired/Blue/blue/set.png" alt="set" width="80%">
You can get flag after traveling through the directory and grab the flags.<br>
<img src="https://github.com/laiyutong/HackTheBox/blob/main/Retired/Blue/blue/getflag.png" alt="getflag" width="60%">

<h2>SUBMIT FLAG</h2>
<h3>Method 2 - Shell</h3>

