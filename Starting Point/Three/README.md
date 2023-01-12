<h1>Three</h1>

<h2>CONNECT</h2>
Connect to Starting Point VPN before starting the machine<br>
<img src="https://github.com/laiyutong/HackTheBox/blob/main/Starting%20Point/Fawn/Fawn/download.png" alt="download" width="30%">
Using <code>openvpn</code> to operate the file of <code>download vpn</code> in kali.

<h2>TASK</h2>

<h3>TASK 1</h3>
Q：How many TCP ports are open?<br>
A：<code>2</code><br>
<img src="https://github.com/laiyutong/HackTheBox/blob/main/Starting%20Point/Crocodile/crocodile/-sC.png" alt="-sC" width="60%">

<h3>TASK 2</h3>
Q：What is the domain of the email address provided in the "Contact" section of the website?<br>
A：<code>thetoppers.htb</code><br>


<h3>TASK 3</h3>
Q：In the absence of a DNS server, which Linux file can we use to resolve hostnames to IP addresses in order to be able to access the websites that point to those hostnames?<br>
A：<code>/etc/hosts</code><br>

<h3>TASK 4</h3>
Q：Which sub-domain is discovered during further enumeration?<br>
A：<code>s3.thetoppers.htb</code><br><br>
<pre text="class">
vhost                     Uses VHOST enumeration mode 
-u, --url string          The target URL
-w, --wordlist string     Path to the wordlist
</pre>

<b>Note</b>: <br>
If using Gobuster version <code>3.2.0 and above</code> we also have to add the <code>--append-domain</code> flag to our
command so that the enumeration takes into account the known vHost ( thetoppers.htb ) and appends it
to the words found in the wordlist ( word.thetoppers.htb ).

<h3>TASK 5</h3>
Q：Which service is running on the discovered sub-domain?<br>
A：<code>admin</code><br><br>

<pre text="class">
Install awscli on Linux：
    apt-get update
    apt-get install awscli
</pre>

First, we need to configure awscli using the following command.<br>
<code>aws configure</code><br>
<a href="https://docs.aws.amazon.com/cli/latest/reference/configure/">Abourt aws configure</a>

list all of the S3 buckets hosted by the server by using the ls command.<br>
<code>aws --endpoint=http://s3.thetoppers.htb s3 ls</code><br>

<h3>TASK 6</h3>
Q：Which command line utility can be used to interact with the service running on the discovered sub-domain?<br>
A：<code>2.4.41</code>

<h3>TASK 7</h3>
Q：Which command is used to set up the AWS CLI installation?<br>
A：<code>wappalyzer</code>

<h3>TASK 8</h3>
Q：What is the command used by the above utility to list all of the S3 buckets?<br>
A：<code>-x</code><br>

<h3>TASK 9</h3>
Q：What is the command used by the above utility to list all of the S3 buckets?<br>
A：<code>login.php</code>
<img src="https://github.com/laiyutong/HackTheBox/blob/main/Starting%20Point/Crocodile/crocodile/dirsearch.png" alt="dirsearch" width="60%">

<h2>SUBMIT FLAG</h2>
