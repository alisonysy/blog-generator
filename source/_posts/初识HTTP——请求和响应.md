---
title: 初识HTTP——请求和响应
date: 2019-01-11 15:43:22
tags: HTTP
---

**HTTP**, aka Hypertext Transfer Protocol, 意为超文本传输协议。
何为*超文本*？个人理解是：从前一向的文字记录是一种有先后/时间/逻辑顺序的语言组织，而超文本则可以将不同的离散信息以创建者指定的方式*非线性*地储存和组织起来。通过超链接，读者可以随意跳离当前信息，到超链接指定的新信息。
何为*传输协议*？当我们需要在万维网WWW浏览一个网页时，浏览器Browser作为客户端Client，会通过一个唯一的地址URL(aka Uniform Resource Locator)向Web服务器Server发起请求。服务器接收到请求后，会对这个客户端作出一定的响应。为确保客户端和服务器之间交流顺畅，大家都能get到对方的意思，我们就需要HTTP协议来规定A代表xxx，而不是yyy，B代表zzz等等。


## HTTP请求
请求Request，是当浏览器/客户端*需要*某些东西，如浏览一个网页、查看一张图片时，告诉服务器“我想做……”。

  ### 用Chrome查看HTTP请求内容
  当我们正在打开一个网页时，我们如何知道浏览器向服务器发送了哪些请求呢？
  ——
  打开Chrome
  在网页显示空白处右击，点击“查看”
  点击图中的“Network”
  在浏览器地址栏输入一个网址，如www.baidu.com
  点击在Network中显示的第一个
  找到Request Headers，点击view source，即可看到请求的内容
  ![“查看”界面的一部分](https://github.com/alisonysy/alisonysy.github.io/blob/master/img/3_1.png?raw=true "查看")

  客户端发出的请求需要按照一定的规则来请求，其中需包含的信息有：

  1. 动词 路径 协议/版本
  2. Key1: value1
  2. Key2: value2
  .. (第二部分可有多个key: value)
  3. 空行
  4. 要上传的数据 (第四部分可有可无)

  第一部分的动词常见的有：
  GET 表示从服务器获取资源
  POST 表示在服务器上传资源
  PUT 表示在服务器上更新*全部*资源
  PATCH 表示在服务器上更新*部分*资源
  DELETE 表示从服务器删除资源

  若没有请求相关路径，则路径默认为 /


## HTTP响应
响应Response，当服务器接收到浏览器的请求并找到/没有找到相应的资源后，会给浏览器所需要的资源或通知浏览器哪里出现了问题。

  ### 用Chrome查看HTTP响应内容
  和用Chrome查看HTTP请求内容相似，唯一不同的是需要找到Response Headers，再点击view source。

  响应的格式为：
  1. 协议/版本号 状态码 状态解释
  2. Key1: value1
  2. Key2: value2
  ..
  3. 空行
  4. 要下载的内容

  其中，不同的状态码表示不同的响应类型，如2XX的状态码表示请求成功，3XX的状态码表示客户端需采取别的操作才能完成请求，具体请看[维基百科的HTTP状态码](https://zh.wikipedia.org/wiki/HTTP%E7%8A%B6%E6%80%81%E7%A0%81 "HTTP状态码-维基")

---

## Git Bash中使用curl命令执行HTTP协议的请求和响应
打开Git Bash后，运行：
> curl -s -v -H *"xxx"* -- "url"

斜体 *"xxx"* 的部分可有可无。如：
![curl命令例子](https://github.com/alisonysy/alisonysy.github.io/blob/master/img/3_2.png?raw=true "curl命令")

这时，向url所在的服务器发起请求，获取该网页。之后，会返回如下信息：
![HTTP请求和响应](https://github.com/alisonysy/alisonysy.github.io/blob/master/img/3_3.png?raw=true "HTTP请求和响应")

如图，以 **>** 开头的行表示浏览器请求的信息：
> GET / HTTP/1.1 
*此行为第一部分*
> Host: www.baidu.com
> User-Agent: curl/7.55.0
> Accept: */*
> hhh: xxx 
*此行及以上为第二部分*
>
> *上面是第三部分的空行*

图中因为只是从服务器中获取，并没有数据的上传，因此没有第四部分。

以 **<** 开头的行表示服务器返回的信息：
> HTTP/1.1 200 OK
*此行为第一部分，200表示请求成功*
> Accept-Ranges: bytes
> .. *此处省略*
> Content-Length: 2443 
> Content-Type: text/html *此处表示了第四部分返回的格式*
> 
> *上面是第三部分的空行*
> <!DOCTYPE> ..
> *空行后面是第四部分下载的内容*



