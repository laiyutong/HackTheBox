<h1>Redeemer</h1>

<h2>CONNECT</h2>
Connect to Starting Point VPN before starting the machine<br>
<img src="https://github.com/laiyutong/HackTheBox/blob/main/Starting%20Point/Fawn/Fawn/download.png" alt="download" width="30%">
Using <code>openvpn</code> to operate the file of <code>download vpn</code> in kali.

<h2>TASK</h2>

<h3>TASK 1</h3>
Q：Which TCP port is open on the machine?<br>
A：<code>6379</code><br>
<img src="https://github.com/laiyutong/HackTheBox/blob/main/Starting%20Point/Redeemer/Redeemer/nmaptcp.png" alt="nmaptcp" width="70%">
<pre class="text">
Parameter Description
-p-: All port
-A: Enable OS detection, version detection, script scanning, and traceroute.</pre>

<h3>TASK 2</h3>
Q：Which service is running on the port that is open on the machine?<br>
A：<code>redis</code><br>
<img src="https://github.com/laiyutong/HackTheBox/blob/main/Starting%20Point/Redeemer/Redeemer/nmaptcp.png" alt="nmaptcp" width="70%">

<h3>TASK 3</h3>
Q：What type of database is Redis?<br>
Choose from the following options:(i) In-memory Database, (ii) Traditional Database<br>
A：<code>In-memory Database</code><br>
<a href="https://redis.io/">Redis</a>, the open source,in-memory data store used by millions of developers as a database, cache, streaming engine, and message broker.

<h3>TASK 4</h3>
Q：Which command-line utility is used to interact with the Redis server?<br> 
Enter the program name you would enter into the terminal without any arguments.<br>
A：<code>redis-cli</code><br>

<h3>TASK 5</h3>
Q：Which flag is used with the Redis command-line utility to specify the hostname?<br>
A：<code>-h</code>

<h3>TASK 6</h3>
Q：Once connected to a Redis server,<br>
which command is used to obtain the information and statistics about the Redis server?<br>
A：<code>info</code>

<h3>TASK 7</h3>
Q：What is the version of the Redis server being used on the target machine?<br>
A：<code>5.0.7</code>
<img src="https://github.com/laiyutong/HackTheBox/blob/main/Starting%20Point/Redeemer/Redeemer/redisinfo.png" alt="connect" width="30%">

<h3>TASK 8</h3>
Q：Which command is used to select the desired database in Redis?<br>
A：<code>select</code>

<h3>TASK 9</h3>
Q：How many keys are present inside the database with index 0?<br>
A：<code>4</code>

<h3>TASK 10</h3>
Q：Which command is used to obtain all the keys in a database?<br>
A：<code>keys *</code>

<h2>SUBMIT FLAG</h2>

<img src="https://github.com/laiyutong/HackTheBox/blob/main/Starting%20Point/Redeemer/Redeemer/flag.png" alt="flag" width="30%">
