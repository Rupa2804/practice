127.0.0.1:6379> INCR login_count
127.0.0.1:6379> HSET user:101 name "Mourya" email "mourya@gmail.com" role "student"
(integer) 3
127.0.0.1:6379> HGET user:101 email
"mourya@gmail.com"
127.0.0.1:6379> HGETALL user:101
1) "name"
2) "Mourya"
3) "email"
4) "mourya@gmail.com"
5) "role"
6) "student"
127.0.0.1:6379> LPUSH tasks "Task A"
(integer) 1
127.0.0.1:6379> RPUSH tasks "Task B"
(integer) 2
127.0.0.1:6379> LRANGE tasks 0 -1
1) "Task A"
2) "Task B"
127.0.0.1:6379> SADD skills "python"
(integer) 1
127.0.0.1:6379> SADD skills "redis"
(integer) 1
127.0.0.1:6379> SMEMBERS skills
1) "redis"
2) "python"
127.0.0.1:6379> ZADD leaderboard 950 rupa
(integer) 1
127.0.0.1:6379> ZADD leaderboard 960 mourya
(integer) 1
127.0.0.1:6379> ZREVRANGE leaderboard 0 -1 WITHSCORES
1) "mourya"
2) "960"
3) "rupa"
4) "950"
127.0.0.1:6379> SUBSCRIBE notifications
Reading messages... (press Ctrl-C to quit)
1) "subscribe"
2) "notifications"
3) (integer) 1
^C
C:\Users\govar>PUBLISH notifications "New course available"
'PUBLISH' is not recognized as an internal or external command,
operable program or batch file.

C:\Users\govar>PUBLISH notifications "New course available"
'PUBLISH' is not recognized as an internal or external command,
operable program or batch file.

C:\Users\govar>SET otp:user101 482931 EX 100
Environment variable otp:user101 482931 EX 100 not defined

C:\Users\govar>SET otp:user101=482931

C:\Users\govar>echo %otp_user101%
%otp_user101%

C:\Users\govar>SET otp_user101=482931

C:\Users\govar>echo %otp_user101%
482931

C:\Users\govar>otp:user101 482931 EX 100
The filename, directory name, or volume label syntax is incorrect.

C:\Users\govar>redis-cli
127.0.0.1:6379> SET otp:user101 482931 EX 100
OK
127.0.0.1:6379> GET otp:user101
"482931"
127.0.0.1:6379> TTL otp:user101
(integer) 69
127.0.0.1:6379>