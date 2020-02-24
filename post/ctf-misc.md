---
title: 攻防世界-misc
date: 2019-10-19 17:40:25
tags:
---
如来十三掌-菜狗为了打败菜猫，学了一套如来十三掌。
与佛论禅”网站，一个编码/解码网站
佛曰：......
![](1.png)
尝试使用Rot13这个明文的形式,但解密之后还是乱码
![](2.png)

然后将得到的结果再进行base64解密，得到flag

![](3.png)




---

pdf-菜猫给了菜狗一张图，说图下面什么都没有

将图片拖走。。。
![](4.png)

![](5.png)
得到答案。。。。

---
功夫再高也怕菜刀

---
对小白的详细补充
foremost是一个文件分离和还原的工具
foremost的[下载](https://github.com/raddyfiy/foremost)及使用
http://q0o0p.top/2019/11/19/cft-tool/

---
用foremost 分离文件，得到一个压缩包，里面有一个加密的flag.txt
![](7.png)
然后用wireshark打开文件，分组字节流查找flag.txt
![](8.png)
![](9.png)
分组字节流搜索6666.jpg，并追踪TCP流。
![](10.png)
找到jpg文件的文件头(FFD8)和文件尾(FFD9)并复制
插入到一个十六进制编辑软件中（这个是[HxD Hex Editor]( https://mh-nexus.de/en/hxd/)），并保存为.jpg的格式
![](11.png)
![](12.png)
打开该图片得到密码
![](13.png)
然后根据密码打开压缩包，得到flag。。。


---

