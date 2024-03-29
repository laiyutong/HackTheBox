<h1>
Oopsie
</h1>

<h2>CONNECT</h2>
Connect to Starting Point VPN before starting the machine<br>
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
<img src="https://github.com/laiyutong/HackTheBox/blob/main/Starting%20Point/TIER%202/Oopsie/Oopsie/nmap.png" alt="nmap" width="60%">
<img src="https://github.com/laiyutong/HackTheBox/blob/main/Starting%20Point/TIER%202/Oopsie/Oopsie/website.png" alt="website" width="60%">
We can find there is a directory <code>/cdn-cgi/login</code> by using <code>BurpSuite</code>.<br>
<img src="https://github.com/laiyutong/HackTheBox/blob/main/Starting%20Point/TIER%202/Oopsie/Oopsie/burpsuite.png" alt="burpsuite" width="60%">
Go back to webpage and add the postfix <code>/cdn-cgi/login</code> to the URL.<br>
It will display a login page, we do not have account yet, so click <code>Login as Guest</code><br>
<img src="https://github.com/laiyutong/HackTheBox/blob/main/Starting%20Point/TIER%202/Oopsie/Oopsie/loginpage.png" alt="loginpage" width="60%">
After clicking "Login as Guest", it will be as shown in the figure below.<br>
Click the menu in the upper right corner, and you can click "Account", "Branding", "Clients", "Uploads" at will, first click "Account".<br>
<img src="https://github.com/laiyutong/HackTheBox/blob/main/Starting%20Point/TIER%202/Oopsie/Oopsie/menu_account.png" alt="menu_account" width="60%">

It is obvious that there is an <code>id=2</code> in the URL part, try to replace it with <code>id=1</code>.<br>
<img src="https://github.com/laiyutong/HackTheBox/blob/main/Starting%20Point/TIER%202/Oopsie/Oopsie/id%3D2.png" alt="id_2" width="60%">

It can be found that the Access ID becomes <code>34322</code>, and the Name becomes <code>admin</code>.<br>
<img src="https://github.com/laiyutong/HackTheBox/blob/main/Starting%20Point/TIER%202/Oopsie/Oopsie/id%3D1.png" alt="id_1" width="60%">

Use <code>dirsearch</code> or <code>gobuster</code> to traverse the web to find where the shell can be uploaded.<br>
<b>cmd</b>：<code>dirsearch -u &lt;target_ip&gt; -e php</code><br>
<img src="https://github.com/laiyutong/HackTheBox/blob/main/Starting%20Point/TIER%202/Oopsie/Oopsie/dirsearch.png" alt="dirsearch" width="50%"><br>
<b>cmd</b>：<code>gobuster dir -u &lt;target_ip&gt; -w /usr/share/dirb/wordlists/common.txt -x .php</code><br>
<img src="https://github.com/laiyutong/HackTheBox/blob/main/Starting%20Point/TIER%202/Oopsie/Oopsie/gobuster.png" alt="gobuster" width="50%"><br>

Go to <code>http://&lt;target_ip&gt;/uploads</code> and you will see "This action requires super admin rights".<br>
It is thought that it may be related to the <code>Access ID/Name</code> in the account just now.<br>
It's might have something to do with cookies.<br>
Open <code>Devtools</code> ⇒ <code>storage</code> ⇒ <code>cookie</code>, and see the current value: <code>guest/2233</code>
<img src="https://github.com/laiyutong/HackTheBox/blob/main/Starting%20Point/TIER%202/Oopsie/Oopsie/Dev_storage.png" alt="Dev_storage" width="60%"><br>

Replace value with：<code>admin/34322</code> and refresh the page,<br>
you can see that the left part of the page allows us to upload files.<br>
Then you can <code>upload the reverse shell</code>.<br>
<img src="https://github.com/laiyutong/HackTheBox/blob/main/Starting%20Point/TIER%202/Oopsie/Oopsie/Dev_admin.png" alt="Dev_admin" width="60%"><br>

Usually the location of the webshell on this machine will be <code>/usr/share/webshells</code>.<br>
The reverse shell to be used here will be under <code>/usr/share/webshells/php</code>.<br>
<img src="https://github.com/laiyutong/HackTheBox/blob/main/Starting%20Point/TIER%202/Oopsie/Oopsie/reverseshell.png" alt="reverseshell" width="60%"><br>
Change the <code>ip</code> and the <code>port</code> in <code>/usr/share/webshells/php/php-reverse-shell.php</code>.<br>
<img src="https://github.com/laiyutong/HackTheBox/blob/main/Starting%20Point/TIER%202/Oopsie/Oopsie/changeip_port.png" alt="changeip_port" width="30%"><br>
<code>Upload</code> the newly changed php-reverse-shell.php to the webpage.<br>
<img src="https://github.com/laiyutong/HackTheBox/blob/main/Starting%20Point/TIER%202/Oopsie/Oopsie/uploaded.png" alt="uploaded" width="60%"><br>
First open a new <code>nc</code> window, then go to the web page URL and enter <code>http://&lt;target_ip&gt;/uploads/php-reverse-shell.php</code>.<br>
Go back to <code>nc</code> window to get shell.<br>
<img src="https://github.com/laiyutong/HackTheBox/blob/main/Starting%20Point/TIER%202/Oopsie/Oopsie/nc.png" alt="nc" width="60%"><br>
Using <code>python3 -c 'import pty;pty.spawn("/bin/bash")'</code> to get <code>interactive</code> shell.<br>
You can find the <code>user.txt</code> in <code>/home/robert</code>！<br>
<img src="https://github.com/laiyutong/HackTheBox/blob/main/Starting%20Point/TIER%202/Oopsie/Oopsie/user.txt.png" alt="user.txt" width="60%"><br>

<h2>Laveral Movement</h2>
Neither sudo -l nor su robert login has sufficient credentials or password.<br>
<img src="https://github.com/laiyutong/HackTheBox/blob/main/Starting%20Point/TIER%202/Oopsie/Oopsie/sudofail.png" alt="sudofail" width="40%">
Continue to find useful information first, because there is not much information.<br>
cd <code>/var/www/html</code> ⇒ cd <code>/cdn-cgi</code> ⇒ cd <code>/login</code> <br>
From the relevant location of the web page, you can see that there are four files under login,<br>
and <code>db.php</code> provides the account secret：<code>robert：M3g4C0rpUs3r!</code><br>
<img src="https://github.com/laiyutong/HackTheBox/blob/main/Starting%20Point/TIER%202/Oopsie/Oopsie/robert.png" alt="robert" width="60%">
Try the login method above again, but still can't log in successfully.<br>
It's possible that this login method is denied/not available, so let's try another method.<br><br>
Recall that the ip has <code>port 22</code> open, so try to use ssh to log in to the account of the robert.<br>
Connection method: <code>ssh &lt;account_name&gt;@&lt;target_ip&gt;</code><br>
<img src="https://github.com/laiyutong/HackTheBox/blob/main/Starting%20Point/TIER%202/Oopsie/Oopsie/ssh.png" alt="ssh" width="60%">
After successful login, enter the id to find that the groups except 1000(robert),<br>
there is also a <code>1001 (bugtracker)</code>, further research on bugtracker.<br><br>
Use <code>ls -al bugtracker</code> to find that user has suid permissions.<br>
<code>suid</code> means that it can be executed with the <code>highest authority (root)</code>.<br>
<img src="https://github.com/laiyutong/HackTheBox/blob/main/Starting%20Point/TIER%202/Oopsie/Oopsie/llbugtracker.png" alt="llbugtracker" width="60%"><br>
Found that bugtracker is an <code>executable</code> program.<br>
No matter what is entered after provide Bug ID, the result will be output as <code>cat /root/reports</code>.<br>
<img src="https://github.com/laiyutong/HackTheBox/blob/main/Starting%20Point/TIER%202/Oopsie/Oopsie/robert_locate_bugtracker.png" alt="robert_locate_bugtracker" width="60%">
<img src="https://github.com/laiyutong/HackTheBox/blob/main/Starting%20Point/TIER%202/Oopsie/Oopsie/bugtracker_hello.png" alt="bugtracker_hello" width="40%">

Normally, calling <code>cat</code> should be under <code>/bin</code>.<br>
From this info we know that we can create a <code>malicious cat command</code>,<br>
but first replace the path of <code>EXPORT</code> (environment variable).<br>
Here, set the <code>/tmp</code> directory as the current environment variable, and then switch to the /tmp directory.<br>

Create a malicious cat command <code>/bin/sh</code> and give the cat execution permission,<br>
when bugtracker is executed, cat under <code>/tmp</code> will be executed,
permissions will change from robert to root.<br>
You can get the root.txt under /root.<br>
<img src="https://github.com/laiyutong/HackTheBox/blob/main/Starting%20Point/TIER%202/Oopsie/Oopsie/previledgeupdate.png" alt="previledgeupdate" width="60%"><br>

<img src="https://github.com/laiyutong/HackTheBox/blob/main/Starting%20Point/TIER%202/Oopsie/Oopsie/root.txt2.png" alt="root.txt2" width="40%"><br>
