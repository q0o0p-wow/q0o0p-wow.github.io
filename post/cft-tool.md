---
title: cft-tool
date: 2019-11-19 16:17:06
tags:
---
## nmap

https://blog.csdn.net/qq_36119192/article/details/82079150

---
## foremost-->文件分离和还原工具
是一个控制台程序，用于文件分离和还原
根据页眉，页脚和内部数据结构恢复文件，可以处理图像文件（例如由dd，Safeback，Encase等生成的图像文件）这些内置类型查看给定文件格式的数据结构，从而实现更可靠，更快速的恢复。
或直接在驱动器上。页眉和页脚可以由配置文件指定，也可以使用命令行开关指定内置文件类型。

在数字取证中和CTF中常用来恢复、分离文件。它默认支持19种类型文件(jpg, gif, png, bmp, avi, exe, mpg, mp4, wav, riff, wmv, mov, pdf, ole, doc, zip, rar, html, cpp 等文件)的扫描识别恢复，还可以通过(通过配置它的配置文件foremost.conf)增加新的支持类型。

windows下载地址 --> https://github.com/raddyfiy/foremost
可以选择自己源码编译为exe，也可以直接用大佬们编译完的（在binary里面）
![](1.png)
将foremost.conf 和 foermost.exe 单独分离出来放入一个新文件夹中
![](2.png)
使用时将要分离的文件放入该文件夹下
![](3.png)
分离完成的后文件-->如果没有指定路径，则放入output里面.


Linux下对于压缩包形式：
```Linux
$ tar zxvf foremost-xx.tar.gz
$ cd foremost-xx
$ make
$ make install
```

直接安装（根据自己的Linux版本）
```linux
$ apt-get install foremost  //Ubuntu安装foremost
$ foremost -h  //检查是否安装成功
$ foremost [-v|-V|-h|-T|-Q|-q|-a|-w-d] [-t <type>] [-s <blocks>] [-k <size>] 
    [-b <size>] [-c <file>] [-o <dir>] [-i <file] 
    //命令及作用

-V  - 显示版权信息并退出  
-t  - 指定文件类型.  (-t jpeg,pdf ...) 
-d  -打开间接块检测 (针对UNIX文件系统) 
-i  - 指定输入文件 (默认为标准输入) 
-a  - 写入所有的文件头部, 不执行错误检测(损坏文件) 
-w  - 向磁盘写入审计文件，不写入任何检测到的文件
-o  - 设置输出目录 (默认为为输出)
-c  - 设置配置文件 (默认为 foremost.conf)
-q  - 启用快速模式. 在512字节边界执行搜索.
-Q  - 启用安静模式. 禁用输出消息. 
-v  - 详细模式. 向屏幕上记录所有消息。
```

注： 未指定输出目录，结果放在foremost所在目录的output文件夹内，配置文件为所在目录的foremost.conf。

---
## Wireshark

[官网下载地址](https://www.wireshark.org/download.html)

[1. burpsuite和Wireshark的原理及区别](https://blog.csdn.net/Zhou_ZiZi/article/details/84987259)
[2. Wiresharkd的详细分析](https://blog.csdn.net/qq78069460/article/details/79153895)

---
HxD Hex Editor
专门用于文件十六进制显示和编辑的软件
免费的，且功能强其功能比Notepad++的插件强
https://mh-nexus.de/en/downloads.php?product=HxD20



参考：https://blog.csdn.net/john_david_/article/details/87273152