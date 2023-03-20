<h1>Legacy</h1>

<h2>CONNECT</h2>
Connect to Starting Point VPN before starting the machine<br>
Using <code>openvpn</code> to operate the file of <code>download vpn</code> in kali.

<h2>SUBMIT FLAG</h2>
Using nmap to scan, we can find  <code>135</code>,  <code>139</code>,  <code>445</code> port are open.<br>
<b>command</b>：<code>nmap -sC -sV &lt;ip&gt;</code>
<img src="https://github.com/laiyutong/HackTheBox/blob/main/Retired/Legacy/Legacy/nmap.png" alt="nmap" width="60%">

Next, using nmap  <code>vuln scripts</code> to check for known vulnerabilities in service.<br>
<b>command</b>：<code>nmap --script=vuln -sC -sV &lt;ip&gt; -p &lt;port&gt;</code><br>
The vulnerable script scans out as <code>MS08-067</code> and <code>ms17-010</code>.<br>
<img src="https://github.com/laiyutong/HackTheBox/blob/main/Retired/Legacy/Legacy/vuln.png" alt="vuln" width="60%">

Open metasploit framework console and search the vulnerability.<br>
<pre text="class">
<b>command</b>：
  <code>msfconsole</code>
  <code>search &lt;vulnerability&gt;</code>
</pre>
<img src="https://github.com/laiyutong/HackTheBox/blob/main/Retired/Legacy/Legacy/msfconsole.png" alt="msfconsole" width="60%">

<b>command</b>：<code>use &lt;Name of Matching Modules&gt;</code><br>
<img src="https://github.com/laiyutong/HackTheBox/blob/main/Retired/Legacy/Legacy/showoptions.png" alt="showoptions" width="60%">

Setting the target ip , local ip, etc.<br>
<img src="https://github.com/laiyutong/HackTheBox/blob/main/Retired/Legacy/Legacy/set.png" alt="set" width="60%">

You can enter <code>help</code> to see the parameter and description.<br>
<img src="https://github.com/laiyutong/HackTheBox/blob/main/Retired/Legacy/Legacy/help.png" alt="help" width="60%">

After exploit successfully, you can get flags by traveling through the directory！<br>
<img src="https://github.com/laiyutong/HackTheBox/blob/main/Retired/Legacy/Legacy/usertxt.png" alt="usertxt" width="40%"><br>
<img src="https://github.com/laiyutong/HackTheBox/blob/main/Retired/Legacy/Legacy/roottxt.png" alt="roottxt" width="40%">

