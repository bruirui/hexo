---
title: HTTP缓存
urlname: article9
date: 2018-08-29 11:29:50
tags: HTTP
---

> [<font color="#456782">HTTP缓存分类</font>](#1)
  [<font color="#456782">浏览器根据什么判断使用强制缓存？</font>](#2)
  [<font color="#456782">服务端是如何判断资源是否过期的？</font>](#3)

<h3 id="1">1.HTTP缓存分类</h3>

|  | 强制缓存 | 对比缓存(协商缓存) |
| :------ | :------ | :------ |
| 定义 | 强制缓存是指如果浏览器中存在缓存数据并且数据没有过期，就直接从缓存中读取数据，无需向服务器发请求 | 对比缓存指如果浏览器中存在缓存数据，则必须向服务器发起请求以询问该数据是否过期，从而决定是否使用本地缓存 |

<h3 id="2">2.浏览器根据什么判断使用强制缓存？</h3><font color="#9e845a">注意：如果Expires和Cache-Control同时存在，Cache-Control优先级高于Expires(建议2个都写，兼容http版本)</font>
主要根据2个HTTP响应头判断：<font color="#9e845a">Expires和Cache-Control</font>
Expires(HTTP1.0)值是服务端设置的资源过期时间，如果当下时间早于过期时间，则直接使用缓存资源。但因为服务端设置的过期时间是绝对时间，而浏览器跟服务器的时间可能不一致，可能会产生误差，所以Expires响应头已经用的比较少了。
Cache-Control(HTTP1.1)值有如下几个: privare(默认值)、public、no-cache、max-age、no-store。
private：指客户端可以缓存
public：指客户端和代理服务器都可以缓存
No-cache：指需要使用对比缓存来验证缓存数据
No-store：指所有内容都不会缓存，强制缓存和对比缓存都不会触发
Max-age=xxx：指缓存的内容将在xxx秒后失效(相对时间)

<h3 id="3">3.服务端是如何判断资源是否过期的？</h3><font color="#9e845a">注意：如果Etag和Last-Modified同时存在，Etag优先级高于Last-Modified</font>
主要通过响应头和请求头间进行传递，服务端通过缓存标识判断资源是否过期。
① <font color="#9e845a">Last-Modified响应头和If-Modified-Since请求头</font>
Last-Modified值表示资源的最后修改时间，在浏览器第一次发起HTTP请求时，服务器会返回该响应头。
浏览器在下次发起HTTP请求时，会带上If-Modified-Since，其值就是Last-Modified的值。
服务器收到请求后会将请求头If-Modified-Since的值和被请求资源的最后修改时间进行比对。若资源的最后修改时间大于If-Modified-Since，说明该资源已被改动过，则响应完整的资源，返回状态码200；若小于或等于，说明资源未被修改，则响应304，告知浏览器继续使用缓存内容。
② <font color="#9e845a">Etag响应头和If-None-Match请求头</font>
Etag响应头的值为当前资源在服务器的唯一标识，在浏览器第一次发起HTTP请求时，服务器会返回该响应头。
当浏览器下次发起请求该资源时，会带上If-None-Match请求头，其值为第一次请求服务器返回的Etag值。
服务器收到请求后发现有请求头If-None-Match则与被请求资源的唯一标识进行比对。若不同，说明资源被改动，响应完整的资源内容，返回状态码200；若相同，则说明未被改动，响应304，告知浏览器使用缓存内容

### HTTP缓存流程图
```flow
st=>start: 发起请求|past:>http://www.google.com[blank]
e=>end: 呈现:>http://www.google.com
c1=>condition: 是否有缓存?
sub1=>operation: 200,向web服务器发送请求,请求响应,缓存协商
c2=>condition: Cache-Control过期?
c3=>condition: Expires过期?
c4=>condition: 存在Etag?
sub2=>operation: 向服务器请求带If-None-Match
c5=>condition: 存在Last-Modified?
sub3=>operation: 向服务器请求带if-Modified-Since
c6=>condition: 是否过期200or304?
sub4=>operation: 304,从缓存读取

st->c1(no)->sub1
c1(yes,left)->c2
c2(yes)->c3(no)->sub4
c2(no)->sub4
c3(yes)->c4
c4(yes)->sub2->c6
c4(no)->c5(yes)->sub3->c6
c5(no)->sub1
c6(yes)->sub1
c6(no)->sub4->e
sub1->e
```
