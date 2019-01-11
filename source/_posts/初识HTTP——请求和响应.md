---
title: 初识HTTP——请求和响应
date: 2019-01-11 15:43:22
tags: HTTP
---
![作业题目](https://github.com/alisonysy/blog-generator/blob/master/source/_images/try.png "homework")

**HTTP**, aka Hypertext Transfer Protocol, 意为超文本传输协议。
何为*超文本*？个人理解是：从前一向的文字记录是一种有先后/时间/逻辑顺序的语言组织，而超文本则可以将不同的离散信息以创建者指定的方式*非线性*地储存和组织起来。通过超链接，读者可以随意跳离当前信息，到超链接指定的新信息。
何为*传输协议*？当我们需要在万维网WWW浏览一个网页时，浏览器Browser作为客户端Client，会通过一个唯一的地址URL(aka Uniform Resource Locator)向Web服务器Server发起请求。服务器接收到请求后，会对这个客户端作出一定的响应。为确保客户端和服务器之间交流顺畅，大家都能get到对方的意思，我们就需要HTTP协议来规定A代表xxx，而不是yyy，B代表zzz等等。

