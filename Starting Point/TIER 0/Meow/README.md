<h1>Meow</h1>

<h2>CONNECT</h2>
Connect to Starting Point VPN before starting the machine<br>
Using <code>openvpn</code> to operate the file of <code>download vpn</code> in kali.

<h2>TASK</h2>

<h3>TASK 1</h3>
Q：What does the acronym VM stand for?<br>
A：<code>Virtual Machine</code><br>
FYI：<a href="https://www.vmware.com/topics/glossary/content/virtual-machine.html">What is VM?</a>

<h3>TASK 2</h3>
Q：What tool do we use to interact with the operating system in order to issue commands via the command line, such as the one to start our VPN connection?<br> It's also known as a console or shell.<br>
A：<code>terminal</code><br>
FYI：<a href="https://www.computerhope.com/jargon/t/terminal.htm">What is terminal?</a>

<h3>TASK 3</h3>
Q：What service do we use to form our VPN connection into HTB labs?<br>
A：<code>openvpn</code><br>
FYI：<a href="https://www.proofpoint.com/us/threat-reference/vpn">What is VPN?</a>

<h3>TASK 4</h3>
Q：What is the abbreviated name for a 'tunnel interface' in the output of your VPN boot-up sequence output?<br>
A：<code>tun</code><br>

<h3>TASK 5</h3>
Q：What tool do we use to test our connection to the target with an ICMP echo request?<br>
A：<code>ping</code>

<h3>TASK 6</h3>
Q：What is the name of the most common tool for finding open ports on a target?<br>
A：<code>nmap</code><br>
<b>cmd</b>：<code>nmap -sV &lt;IP&gt;</code><br>
<img src="https://i.imgur.com/V9zdcPJ.png" alt="nmap" width="60%">

<h3>TASK 7</h3>
Q：What service do we identify on port 23/tcp during our scans?<br>
A：<code>telnet</code>
<img src="https://i.imgur.com/V9zdcPJ.png" alt="nmap" width="60%">

<h3>TASK 8</h3>
Q：What username is able to log into the target over telnet with a blank password?<br>
A：<code>root</code>

<h2>SUBMIT FLAG</h2>
First, using <code>nmap &lt;TARGET_IP&gt;</code> to find useful port.<br>
Only <code>23 port (telnet)</code> is open.<br>
<img src="https://i.imgur.com/V9zdcPJ.png" alt="nmap" width="60%">
You can connect to remote ip with <code>root</code> by using <code>telnet &lt;TARGET_IP&gt;</code>.
<img src="https://i.imgur.com/zoCsgEf.png" alt="telnet" width="60%">
You can use <code>help</code> to see the commands.
After entering <code>ls</code>, you can see there is a flag.txt.<br>
Finally, you can use <code>cat</code> to get flag！
<img src="https://i.imgur.com/RHLwvUE.png" alt="getflag" width="60%">
