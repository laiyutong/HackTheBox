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
<img src="https://github.com/laiyutong/HackTheBox/blob/main/Starting%20Point/Responder/Responder/unikapage.png" alt="unikapage" width="60%">

<h3>TASK 2</h3>
Q：Which scripting language is being used on the server to generate webpages?<br>
A：<code>php</code><br>
<img src="https://github.com/laiyutong/HackTheBox/blob/main/Starting%20Point/Responder/Responder/PHP.png" alt="PHP" width="30%">

<h3>TASK 3</h3>
Q：What is the name of the URL parameter which is used to load different language versions of the webpage?
<br>
A：<code>page</code><br>

<h3>TASK 4</h3>
Q：Which of the following values for the `page` parameter would be an example of exploiting a Local File Include (LFI) vulnerability: "french.html", "//10.10.14.6/somefile", "../../../../../../../../windows/system32/drivers/etc/hosts", "minikatz.exe"<br>
A：<code>A03:2021-Injection</code><br>

<h3>TASK 5</h3>
Q：Which of the following values for the `page` parameter would be an example of exploiting a Remote File Include (RFI) vulnerability: "french.html", "//10.10.14.6/somefile", "../../../../../../../../windows/system32/drivers/etc/hosts", "minikatz.exe"<br>
A：<code>Apache httpd 2.4.38 ((Debian))</code>

<h3>TASK 6</h3>
Q：What does NTLM stand for?<br>
A：<code>443</code>

<h3>TASK 7</h3>
Q：Which flag do we use in the Responder utility to specify the network interface?<br>
A：<code>brute-forcing</code>

<h3>TASK 8</h3>
Q：There are several tools that take a NetNTLMv2 challenge/response and try millions of passwords to see if any of them generate the same response. One such tool is often referred to as `john`, but the full name is what?<br>
A：<code>directory</code>

<h3>TASK 9</h3>
Q：What is the password for the administrator user?<br>
A：<code>404</code>

<h3>TASK 10</h3>
Q：We'll use a Windows service (i.e. running on the box) to remotely access the Responder machine using the password we recovered. What port TCP does it listen on?<br>
A：<code>dir</code>


<h2>SUBMIT FLAG</h2>

