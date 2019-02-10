---
title: Cookie是块什么‘饼干’？
date: 2019-02-10 13:31:08
tags: HTTP
---

我们浏览网页时，特别是当我们逛某宝、某东时，浏览器怎么把我们之前看过的商品给记下来，还能为我们推荐“猜你喜欢”呢？这就要靠HTTP的cookie。
> Cookie是服务器发送给用户浏览器的小块数据。

浏览器会把这数据保存下来，等下一次，对相同的服务器发出请求时，把之前保存下来的数据一并发送，这样服务端就能知道 **“你是谁”**，**你之前做过什么**，以及**根据你之前做的，我这次应该怎么做**。

### Cookie的用途
1. 会话管理
登陆、购物车、游戏记录等等；
2. 个性化设置
用户个性化设置、主题等等；
3. 追踪
记录和分析用户行为。

### 创建cookie
当服务器接收到一个HTTP请求时，它可以在响应头设置一个Set-Cookie，
```
Set-Cookie: <cookie-name>=<cookie-value>
```
Set-Cookie里的值通常是用户通过浏览器提交的数据，或被浏览器记录的行为。
一个包含着Set-Cookie的响应头可以是这样：
```
HTTP/2.0 200 OK
Content-type: text/html
Set-Cookie: cookie_name=value_stored

[response]
```
从服务端接收到Set-Cookie之后，浏览器会把它保存，等下次浏览器向同样的服务端发起请求时，会自动把这段cookie带上：
```
GET / HTTP/2.0
Host: www.url.com
Cookie: cookie_name=value_stored
```

### 以用户自动登录为栗子
![用户自动登录的cookie](https://i.loli.net/2019/02/10/5c5fbea65410b.png)