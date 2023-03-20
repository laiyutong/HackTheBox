<h1>
Oopsie
</h1>

<h2>CONNECT</h2>
Connect to Starting Point VPN before starting the machine<br>
<img src="https://github.com/laiyutong/HackTheBox/blob/main/Starting%20Point/Fawn/Fawn/download.png" alt="download" width="30%">
Using <code>openvpn</code> to operate the file of <code>download vpn</code> in kali.

<h2>TASK</h2>

<h3>TASK 1</h3>
Q：With what kind of tool can intercept web traffic?<br>
A：<code>proxy</code><br><br>

<h3>TASK 2</h3>
Q：What is the path to the directory on the webserver that returns a login page?<br>
A：<code>/cdn-cgi/login</code><br><br>

<h3>TASK 3</h3>
Q：What can be modified in Firefox to get access to the upload page?<br>
A：<code>cookie</code><br><br>

<h3>TASK 4</h3>
Q：What is the access ID of the admin user?<br>
A：<code>34322</code><br><br>

<h3>TASK 5</h3>
Q：On uploading a file, what directory does that file appear in on the server?<br>
A：<code>/uploads</code><br><br>

<h3>TASK 6</h3>
Q：What is the file that contains the password that is shared with the robert user?<br>
A：<code>db.php</code><br><br>

<h3>TASK 7</h3>
Q：What executible is run with the option "-group bugtracker" to identify all files owned by the bugtracker group?<br>
A：<code>find</code><br><br>

<h3>TASK 8</h3>
Q：Regardless of which user starts running the bugtracker executable, what's user privileges will use to run?<br>
A：<code>root</code><br><br>

<h3>TASK 9</h3>
Q：What SUID stands for?<br>
A：<code>Set owner User ID</code><br><br>

<h3>TASK 10</h3>
Q：What is the name of the executable being called in an insecure manner?<br>
A：<code>cat</code><br><br>

<h2>SUBMIT FLAG</h2>
The <code>port 22(SSH)</code> and <code>port 80(HTTP)</code> are open, therefore, we visit the IP by using the web browser.<br>
<img src="https://github.com/laiyutong/HackTheBox/blob/main/Starting%20Point/Oopsie/Oopsie/nmap.png" alt="nmap" width="60%">
<img src="https://github.com/laiyutong/HackTheBox/blob/main/Starting%20Point/Oopsie/Oopsie/website.png" alt="website" width="60%"><br>
We can find there is a directory <code>/cdn-cgi/login</code> by using <code>BurpSuite</code>.<br>
<img src="https://github.com/laiyutong/HackTheBox/blob/main/Starting%20Point/Oopsie/Oopsie/burpsuite.png" alt="burpsuite" width="60%"><br>
Go back to webpage and add the postfix <code>/cdn-cgi/login</code> to the URL.<br>
It will display a login page, we do not have account yet, so click <code>Login as Guest</code><br>
<img src="https://github.com/laiyutong/HackTheBox/blob/main/Starting%20Point/Oopsie/Oopsie/loginpage.png" alt="loginpage" width="60%"><br>

<img src="https://github.com/laiyutong/HackTheBox/blob/main/Starting%20Point/Oopsie/Oopsie/menu_account.png" alt="menu_account" width="60%"><br>


<img src="https://github.com/laiyutong/HackTheBox/blob/main/Starting%20Point/Oopsie/Oopsie/id%3D2.png" alt="id_2" width="60%"><br>
<img src="https://github.com/laiyutong/HackTheBox/blob/main/Starting%20Point/Oopsie/Oopsie/id%3D1.png" alt="id_1" width="60%"><br>
<img src="https://github.com/laiyutong/HackTheBox/blob/main/Starting%20Point/Oopsie/Oopsie/dirsearch.png" alt="dirsearch" width="50%"><br>
<img src="https://github.com/laiyutong/HackTheBox/blob/main/Starting%20Point/Oopsie/Oopsie/gobuster.png" alt="gobuster" width="50%"><br>
<img src="https://github.com/laiyutong/HackTheBox/blob/main/Starting%20Point/Oopsie/Oopsie/Dev_storage.png" alt="Dev_storage" width="60%"><br>

<img src="https://github.com/laiyutong/HackTheBox/blob/main/Starting%20Point/Oopsie/Oopsie/Dev_admin.png" alt="Dev_admin" width="60%"><br>
<img src="https://github.com/laiyutong/HackTheBox/blob/main/Starting%20Point/Oopsie/Oopsie/reverseshell.png" alt="reverseshell" width="60%"><br>
<img src="https://github.com/laiyutong/HackTheBox/blob/main/Starting%20Point/Oopsie/Oopsie/changeip_port.png" alt="changeip_port" width="30%"><br>
<img src="https://github.com/laiyutong/HackTheBox/blob/main/Starting%20Point/Oopsie/Oopsie/uploaded.png" alt="uploaded" width="60%"><br>
<img src="https://github.com/laiyutong/HackTheBox/blob/main/Starting%20Point/Oopsie/Oopsie/nc.png" alt="nc" width="60%"><br>

<img src="https://github.com/laiyutong/HackTheBox/blob/main/Starting%20Point/Oopsie/Oopsie/user.txt.png" alt="user.txt" width="60%"><br>

<h3>Laveral Movement</h3>
<img src="https://github.com/laiyutong/HackTheBox/blob/main/Starting%20Point/Oopsie/Oopsie/sudofail.png" alt="sudofail" width="60%"><br>
<img src="https://github.com/laiyutong/HackTheBox/blob/main/Starting%20Point/Oopsie/Oopsie/robert.png" alt="robert" width="60%"><br>
<img src="https://github.com/laiyutong/HackTheBox/blob/main/Starting%20Point/Oopsie/Oopsie/ssh.png" alt="ssh" width="60%"><br>
<img src="https://github.com/laiyutong/HackTheBox/blob/main/Starting%20Point/Oopsie/Oopsie/llbugtracker.png" alt="llbugtracker" width="40%"><br>

<img src="https://github.com/laiyutong/HackTheBox/blob/main/Starting%20Point/Oopsie/Oopsie/robert_locate_bugtracker.png" alt="robert_locate_bugtracker" width="60%"><br>
<img src="https://github.com/laiyutong/HackTheBox/blob/main/Starting%20Point/Oopsie/Oopsie/bugtracker_hello.png" alt="bugtracker_hello" width="40%"><br>
<img src="https://github.com/laiyutong/HackTheBox/blob/main/Starting%20Point/Oopsie/Oopsie/previledgeupdate.png" alt="previledgeupdate" width="60%"><br>

<img src="https://github.com/laiyutong/HackTheBox/blob/main/Starting%20Point/Oopsie/Oopsie/root.txt2.png" alt="root.txt2" width="40%"><br>
