# Remote Dictionary Server (redis)

Q: What is the best way to learn redis?
A: Read this: https://raw.githubusercontent.com/redis/redis/unstable/redis.conf

Q: Are keys unique to each database?
A: Yes. `SELECT <n>` switches the context to that database #.

```bash
モ telnet 127.0.0.1 6380
Trying 127.0.0.1...
Connected to localhost.
Escape character is '^]'.
KEYS *
*0
SELECT 0
+OK
GET xlgmokha
$-1
SET xlgmokha "was here"
+OK
GET xlgmokha
$8
was here
SELECT 1
+OK
GET xlgmokha
$-1
SET xlgmokha "dissappear"
+OK
GET xlgmokha
$10
dissappear
SELECT 0
+OK
GET xlgmokha
$8
was here
QUIT
+OK
Connection closed by foreign host.
```

Q. What does the append only file format look like?

```plaintext
*2
$6
SELECT
$1
0
*3
$3
SET
$8
xlgmokha
$8
was here
*2
$6
SELECT
$1
1
*3
$3
SET
$8
xlgmokha
$10
dissappear
```

Q: Is that it?
A: Yup! What more do you want?

Q: Do you like Redis?
A: Yes, I appreciate how simple it is.
