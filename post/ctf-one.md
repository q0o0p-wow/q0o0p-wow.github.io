---
title: 攻防世界-web-oneday
date: 2019-10-05 14:01:14
tags:
---
## 第一题
![](1.png)

1. 该题目可以用F12查看源代码
2. URL地址栏加view-source:  或 Ctrl+u（查看源码快捷键）
下方有个被注释的一串字符串，找到flag
将注释取消，改为：
``` html
cyberpeace{d0d694dd09d7ee5ab0ae4af3d4e7373a}
```
提交
![](2.png)

## 第二题
get_post: X老师告诉小宁同学HTTP通常使用两种请求方法，你知道是哪两种吗？
![](3.png)
打开以后
![](4.png)
### 工具：
### chrome使用postman插件
### 火狐插件hackbar（提交post请求）
F12先点击Load URL然后直接在http://111.198.29.45:39706/后加 ?a=1
然后在勾选Post data 在点击Execute
![](5.png)

## 补充：

GET传值主要在url后面加个问号然后再传参，然后post一般在火狐浏览器用hackbar传值
HTTP协议中共定义了八种方法来表明对Request-URI指定的资源的不同操作方式，具体介绍如下：

·GET：向特定的资源发出请求。

·POST：向指定资源提交数据进行处理请求（例如提交表单或者上传文件）。数据被包含在请求体中。POST请求可能会导致新的资源的创建和/或已有资源的修改。

·OPTIONS：返回服务器针对特定资源所支持的HTTP请求方法。也可以利用向Web服务器发送'*'的请求来测试服务器的功能性。

·HEAD：向服务器索要与GET请求相一致的响应，只不过响应体将不会被返回。这一方法可以在不必传输整个响应内容的情况下，就可以获取包含在响应消息头中的元信息。

·PUT：向指定资源位置上传其最新内容。

·DELETE：请求服务器删除Request-URI所标识的资源。

·TRACE：回显服务器收到的请求，主要用于测试或诊断。

·CONNECT：HTTP/1.1协议中预留给能够将连接改为管道方式的代理服务器。
### 数据提交到服务器一般有两种方式，GET和POST。
GET的优点:
1.执行效率比POST高。
2.可以通过url传递数据，查找数据的时候就会体现到它的好处。

GET的缺点:
1.安全性很低，因为上传的数据都会显示在url上，所以一般用在上传无关紧要的数据上。
2.上传的数据量较小，一般不能超过4K.这也是因为url的长度而被限制的。

POST优点:
1.安全性高，但是也不是很高，如果想要高安全性的话就用https传输协议。
2.上传的数据量比GET大得多。“理论上讲，POST是没有大小限制的，HTTP协议规范也没有进行大小限制，说“POST数据量存在 80K/100K的大小限制”是不准确的，POST数据是没有限制的，起限制作用的是服务器的处理程序的处理能力。”

POST缺点:
1.执行效率比GET低，但是现在的计算机都很强大，这些几乎可以忽略不计，所以建议一般都使用POST方式。
2.不可以通过url传递数据，有时候可能会不方便.

GET一般用于获取/查询资源信息，而POST一般用于更新资源信息。

---
## 第三题
robots-X老师上课讲了Robots协议，小宁同学却上课打了瞌睡，赶紧来教教小宁Robots协议是什么吧。
！[](6.png)

f1ag_1s_h3re.php这个页面不允许被爬取
查看一下f1ag_1s_h3re.php页面得到正确答案

扫目录也可以扫到:
```
python python3 dirsearch.py -u http://10.10.10.175:32793/ -e *
```
这里我们将下载好的[dirsearch](https://github.com/maurosoria/dirsearch)脚本解压后，打开dirsearch.py文件，运行一下，提示需要输入命令：
```
-u http://10.10.10.175:32793/ -e *
```

在.\reports\111.198.29.45\目录下找到刚输出的文件：
打开即可看到扫出的目录和文件。即可看到存在robots.txt文件。
HTML访问robots.txt发现f1ag_1s_h3re.php
访问robots.txt发现f1ag_1s_h3re.php


### 相关介绍：
Robots协议（也称为爬虫协议、机器人协议等）的全称是“网络爬虫排除标准”（Robots Exclusion Protocol），网站通过Robots协议告诉搜索引擎哪些页面可以抓取，哪些页面不能抓取。
robots协议通常以robots.txt存在，robots.txt文件是一个文本文件，robots.txt是一个协议，而不是一个命令。
如果存在，搜索机器人就会按照该文件中的内容来确定访问的范围；
如果该文件不存在，所有的搜索蜘蛛将能够访问网站上所有没有被口令保护的页面。
robots.txt是搜索引擎中访问网站的时候要查看的第一个文件。robots.txt文件告诉蜘蛛程序在服务器上什么文件是可以被查看的。

-----
User-agent: * 这里的代表的所有的搜索引擎种类，是一个通配符
Disallow: /admin/ 这里定义是禁止爬寻admin目录下面的目录
Disallow: /require/ 这里定义是禁止爬寻require目录下面的目录
Disallow: /ABC/ 这里定义是禁止爬寻ABC目录下面的目录
Disallow: /cgi-bin/.htm 禁止访问/cgi-bin/目录下的所有以".htm"为后缀的URL(包含子目录)。
Disallow: /?* 禁止访问网站中所有包含问号 (?) 的网址
Disallow: /.jpg$ 禁止抓取网页所有的.jpg格式的图片
Disallow:/ab/adc.html 禁止爬取ab文件夹下面的adc.html文件。
Allow: /cgi-bin/　这里定义是允许爬寻cgi-bin目录下面的目录
Allow: /tmp 这里定义是允许爬寻tmp的整个目录
Allow: .htm$ 仅允许访问以".htm"为后缀的URL。
Allow: .gif$ 允许抓取网页和gif格式图片
Sitemap: 网站地图 告诉爬虫这个页面是网站地图
-----

## 第四题
backup-X老师忘记删除备份文件，他派小宁同学去把备份文件找出来,一起来帮小宁同学吧

---

常见的备份文件后缀名有: .git .svn .swp  .~ .bak .bash_history（共6种）
.bak是备份文件，为文件格式扩展名，这类文件一般在.bak前面加上应该有原来的扩展名比如windows.dll.bak，或是windows_dll.bak，有的则是由原文件的后缀名和bak混合而成

---

可以使用扫目录脚本或软件,扫一下,这里使用的是github上的脚本dirsearch,命令行下: py python3 dirsearch.py -u http://111.198.29.45:47591 -e *
看到存在备份文件index.php.bak访问 http://10.10.10.175:32770/index.php.bak

下载到本地打开，即可看到flag

---


## 第五题
cookie-X老师告诉小宁他在cookie里放了些东西，小宁疑惑地想：‘这是夹心饼干的意思吗？

---
### 相关介绍：
Cookie 在网络系统中几乎无处不在，当我们浏览以前访问过的网站时，网页中可能会出现 ：你好 XXX，这会让我们感觉很亲切，就好像吃了一个小甜品一样。这其实是通过访问主机中的一个文件来实现的，这个文件就是 Cookie。在 Internet 中，Cookie 实际上是指小量信息，是由Web服务器创建的，将信息存储在用户计算机上的文件。一般网络用户习惯用其复数形式 Cookies，指某些网站为了辨别用户身份、进行Session 跟踪而存储在用户本地终端上的数据，而这些数据通常会经过加密处理。

---

F12 -> 存储-> Cookie-> look here-> look here：cookie.php
在URL后加上"/cookie.php"即http://111.198.29.45:47420/cookie.php

 ![](9.png)

 控制台-> 消息头-> 找到flag
 ![](10.png)

---
## 第六题
disabled_button-X老师今天上课讲了前端知识，然后给了大家一个不能按的按钮，小宁惊奇地发现这个按钮按不下去，到底怎么才能按下去呢？

---
相关介绍:
disabled，借助开发者工具可以删除这些属性，从而让其变得可用

也可以手动POST相关数据，以下为部分源代码：
``` html
<form action="" method="post" >
<input disabled class="btn btn-default" style="height:50px;width:200px;" type="submit" value="flag" name="auth" />
</form>
```

于是构造POST请求：auth=flag
---
F12，将标签input中的disabled（不可用）属性删除，x掉调试框，点击按钮，即可得到flag。
![](11.png)
![](12.png)

---

## 第七题
simple——js-小宁发现了一个网页，但却一直输不对密码。(Flag格式为 Cyberpeace{xxxxxxxxx} )

F12，找index文件，阅读js代码。（或者ctrl+u :view-source命令）
![](13.png)

会发现dechiffre返回值与参数pass_enc没有任何关联，返回值是固定的，即不论输入什么都是一样得输出。
所以猜测密码在string这一行里。
利用python/java代码来求出flag：先将16进制数输出，再将数字（ascii码）转换为对应的字符。




---

## 第八题
xff_referer-X老师告诉小宁其实xff和referer是可以伪造的。

### 相关介绍：

X-Forwarded-For:简称XFF头，它代表客户端，也就是HTTP的请求端真实的IP，只有在通过了HTTP 代理或者负载均衡服务器时才会添加该项。
HTTP Referer是header的一部分，当浏览器向web服务器发送请求的时候，一般会带上Referer，告诉服务器我是从哪个页面链接过来的，服务器基此可以获得一些信息用于处理。

xff 是http的拓展头部，作用是使Web服务器获取访问用户的IP真实地址（可伪造）。由于很多用户通过代理服务器进行访问，服务器只能获取代理服务器的IP地址，而xff的作用在于记录用户的真实IP，以及代理服务器的IP。

格式为：X-Forwarded-For: 本机IP, 代理1IP, 代理2IP, 代理2IP

---
在Proxy的History里找到目标网页，右键选择发送到repeater。在repeater里查看目标地址内容，添加：X-Forwarded-For:123.123.123.123（这一步是伪造XFF———>go-->收到提示）。
或者直接在Proxy的'Intercept is on'里面加上：  X-Forwarded-For:123.123.123.123。
![](14.png)

Referer:https://www.google.com（这一步是伪造Referer）


也可以直接在Host: 111.198.29.45:40025下面写入：
X-Forwarded-For:123.123.123.123
Referer:https://www.google.com

![](15.png)
![](16.png)


---
## 第九题
weak_auth-小宁写了一个登陆验证页面，随手就设了一个密码。

### 相关介绍：

Intruder是一个定制的高度可配置工具，可以对Web应用程序进行自动化攻击。
原理：Intruder在原始请求数据的基础上，通过修改各种请求参数获取不同的请求应答。在每一次请求中，Intruder通常会携带一个或多个有效攻击载荷（Payload），在不同的位置进行攻击重放，通过应答数据的比对分析获得需要的特征数据。

github上密码字典：
https://github.com/rootphantomer/Blasting_dictionary


---
F12可以看到：
![](17.png)
找到Positions，清楚标记Clear，指针指向password=后面，添加标记Add，如下图所示，将密码放在两个 $pass$ 之间。
找到Payloads，加载Load Payload Options，将下载好的字典添加进去。
选择左上角startAttack开始爆破。



登陆以后可以看到:
cyberpeace{e255ee279841e7f1eb8f44a420e01870}
---
## 第十题
webshel-小宁百度了php一句话,觉着很有意思,并且把它放在index.php里。

看到一句话木马，而且题目描述提示一句话木马放在index.php中。
蚂剑（https://github.com/AntSwordProject/antSword/releases）

用菜刀连接:
http://111.198.29.45:58974/index.php










---



参考：https://www.cnblogs.com/kubbycatty/archive/2019/06/27/11100171.html
      https://blog.csdn.net/qq_43081170/article/details/94717446

