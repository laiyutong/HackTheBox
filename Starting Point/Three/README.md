<h1>Three</h1>

<h2>CONNECT</h2>
Connect to Starting Point VPN before starting the machine<br>
<img src="https://github.com/laiyutong/HackTheBox/blob/main/Starting%20Point/Fawn/Fawn/download.png" alt="download" width="30%">
Using <code>openvpn</code> to operate the file of <code>download vpn</code> in kali.

<h2>TASK</h2>

<h3>TASK 1</h3>
Q：How many TCP ports are open?<br>
A：<code>2</code><br><br>
<img src="https://github.com/laiyutong/HackTheBox/blob/main/Starting%20Point/Three/Three/nmap.png" alt="nmap" width="60%">

<h3>TASK 2</h3>
Q：What is the domain of the email address provided in the "Contact" section of the website?<br>
A：<code>thetoppers.htb</code><br><br>
<img src="https://github.com/laiyutong/HackTheBox/blob/main/Starting%20Point/Three/Three/contact.png" alt="-contact" width="60%">

<h3>TASK 3</h3>
Q：In the absence of a DNS server, which Linux file can we use to resolve hostnames to IP addresses in order to be able to access the websites that point to those hostnames?<br>
A：<code>/etc/hosts</code><br>

<h3>TASK 4</h3>
Q：Which sub-domain is discovered during further enumeration?<br>
A：<code>s3.thetoppers.htb</code><br><br>
There are different enumeration tools available like <code>gobuster</code>, <code>wfuzz</code> , <code>feroxbuster</code> etc.<br>
Here I use gobuster for sub-domain enumeration by using the following command.<br>
<pre text="class">
<b>Command</b>:
gobuster vhost -w /opt/useful/SecLists/Discovery/DNS/subdomains-top1million-5000.txt -u
http://thetoppers.htb --apend-domain<br>
<b>Parameter Description</b>:
vhost：Uses VHOST enumeration mode 
-u (--url string)：The target URL
-w (--wordlist string)：Path to the wordlist

<b>Note</b>:
If using Gobuster version <code>3.2.0 and above</code> we also have to add the <code>--append-domain</code> flag to our
command so that the enumeration takes into account the known vHost ( thetoppers.htb ) and appends it
to the words found in the wordlist ( word.thetoppers.htb ).
</pre>

<img src="https://github.com/laiyutong/HackTheBox/blob/main/Starting%20Point/Three/Three/gobuster.png" alt="gobuster" width="60%">
<img src="https://github.com/laiyutong/HackTheBox/blob/main/Starting%20Point/Three/Three/vhost2.png" alt="vhost2" width="60%">

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
<img src="https://github.com/laiyutong/HackTheBox/blob/main/Starting%20Point/Three/Three/awsls.png" alt="awsls" width="60%">

<h3>TASK 9</h3>
Q：What is the command used by the above utility to list all of the S3 buckets?<br>
A：<code>php</code><br><br>

<h2>SUBMIT FLAG</h2>
FYI：About <a href="https://www.tecmint.com/tldr-easy-to-understand-linux-man-pages/">TLDR</a> command<br>

<img src="https://github.com/laiyutong/HackTheBox/blob/main/Starting%20Point/Three/Three/s3thetoppers.png" alt="s3thetoppers" width="60%">
<img src="https://github.com/laiyutong/HackTheBox/blob/main/Starting%20Point/Three/Three/etc_hosts.png" alt="etc_hosts" width="60%">
<img src="https://github.com/laiyutong/HackTheBox/blob/main/Starting%20Point/Three/Three/awsconfigure.png" alt="awsconfigure" width="40%">
<img src="https://github.com/laiyutong/HackTheBox/blob/main/Starting%20Point/Three/Three/awsls.png" alt="awsls" width="60%">
<img src="https://github.com/laiyutong/HackTheBox/blob/main/Starting%20Point/Three/Three/awsls2.png" alt="awsls2" width="60%">
<img src="https://github.com/laiyutong/HackTheBox/blob/main/Starting%20Point/Three/Three/shell.php.png" alt="shell.php" width="60%">
<img src="https://github.com/laiyutong/HackTheBox/blob/main/Starting%20Point/Three/Three/cp_shell.png" alt="cp_shell" width="60%">
<img src="https://github.com/laiyutong/HackTheBox/blob/main/Starting%20Point/Three/Three/awsls3.png" alt="awsls3" width="60%">
<img src="https://github.com/laiyutong/HackTheBox/blob/main/Starting%20Point/Three/Three/cmd%3Did.png" alt="cmdid" width="60%">
<img src="" alt="-sC" width="60%">
<img src="" alt="-sC" width="60%">
<img src="" alt="-sC" width="60%">
<img src="" alt="-sC" width="60%">
