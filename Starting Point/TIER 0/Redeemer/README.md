<h1>Redeemer</h1>

<h2>CONNECT</h2>
Connect to Starting Point VPN before starting the machine<br>
Using <code>openvpn</code> to operate the file of <code>download vpn</code> in kali.

<h2>TASK</h2>

<h3>TASK 1</h3>
Q：Which TCP port is open on the machine?<br>
A：<code>6379</code><br>
<img src="https://i.imgur.com/B3YRa5K.png" alt="nmap" width="60%">

<h3>TASK 2</h3>
Q：Which service is running on the port that is open on the machine?<br>
A：<code>redis</code><br>

<h3>TASK 3</h3>
Q：What type of database is Redis? Choose from the following options:<br>
(i) In-memory Database<br>
(ii) Traditional Database<br>
A：<code>In-memory Database</code><br>
FYI：<a href="https://redis.io/">What is Redis?</a>

<h3>TASK 4</h3>
Q：Which command-line utility is used to interact with the Redis server?<br>
Enter the program name you would enter into the terminal without any arguments.<br>
A：<code>redis-cli</code><br>

<h3>TASK 5</h3>
Q：Which flag is used with the Redis command-line utility to specify the hostname?<br>
A：<code>-h</code>

<h3>TASK 6</h3>
Q：Once connected to a Redis server, which command is used to obtain the information and statistics about the Redis server?<br>
A：<code>info</code><br>
<pre class="text">
<b>Redis-cli commonly used commands</b>
  
String Commands:
SET key value: Set the value for a key.
GET key: Get the value of a key.
DEL key: Delete one or more keys.
INCR key: Increment the integer value of a key by one.
EXPIRE key seconds: Set a key's time to live in seconds.

Hash Commands:
HSET key field value: Set the value of a field in a hash.
HGET key field: Get the value of a field in a hash.
HGETALL key: Get all the fields and values in a hash.
HDEL key field [field ...]: Delete one or more fields from a hash.
HKEYS key: Get all the field names in a hash.

List Commands:
LPUSH key value [value ...]: Prepend one or multiple values to a list.
RPUSH key value [value ...]: Append one or multiple values to a list.
LPOP key: Remove and get the first element in a list.
RPOP key: Remove and get the last element in a list.
LRANGE key start stop: Get a range of elements from a list.

Set Commands:
SADD key member [member ...]: Add one or more members to a set.
SMEMBERS key: Get all the members of a set.
SREM key member [member ...]: Remove one or more members from a set.
SISMEMBER key member: Check if a member exists in a set.

Sorted Set Commands:
ZADD key score member [score member ...]: Add one or more members to a sorted set with scores.
ZRANGE key start stop [WITHSCORES]: Get a range of members from a sorted set.
ZREM key member [member ...]: Remove one or more members from a sorted set.
ZSCORE key member: Get the score of a member in a sorted set.

Miscellaneous Commands:
PING: Ping the Redis server.
INFO: Get information and statistics about the Redis server.
DBSIZE: Get the number of keys in the currently selected database.
FLUSHDB: Delete all keys in the currently selected database.
</pre>
<img src="https://i.imgur.com/E8dJoR6.png" alt="redis-info" width="60%">

<h3>TASK 7</h3>
Q：What is the version of the Redis server being used on the target machine?<br>
A：<code>5.0.7</code>

<h3>TASK 8</h3>
Q：Which command is used to select the desired database in Redis?<br>
A：<code>select</code><br>
<img src="https://i.imgur.com/8BSVFgV.png" alt="key*" width="40%">

<h3>TASK 9</h3>
Q：How many keys are present inside the database with index 0?<br>
A：<code>4</code>

<h3>TASK 10</h3>
Q：Which command is used to obtain all the keys in a database?<br>
A：<code>keys *</code><br>
<img src="https://i.imgur.com/8BSVFgV.png" alt="key*" width="40%">


<h2>SUBMIT FLAG</h2>

<img src="https://i.imgur.com/B3YRa5K.png" alt="nmap" width="60%">
Connect to a remote server on the default port (6379) by using <code>redis-cli -h &lt;TARGET_IP&gt;</code>.<br>
Entering <code>info</code> to get information and statistics about the Redis server.<br>
<img src="https://i.imgur.com/E8dJoR6.png" alt="redis-info" width="60%">
<img src="https://i.imgur.com/tmWdOG6.png" alt="getflag" width="40%">
<img src="" alt="" width="60%">
<img src="" alt="" width="60%">
