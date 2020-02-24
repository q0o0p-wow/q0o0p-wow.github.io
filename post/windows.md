---
title: Windows 常用命令
date: 2019-11-15 10:13:59
tags:
---

转发： https://mp.weixin.qq.com/s/8vt1HsqV5b1H0xMkUK4CiA

0x01：常用系统指令

dir           //查看当前目录和子目录

tree          以图形模式显示驱动器或路径的目录结构

mkdir         创建目录

md           创建文件夹

rd           删除文件夹

move          将文件从一个目录转移到另一个目录

type         显示文本文件内容

copy          复制文件

del          删除文件

quser         查看当前登陆的用户

rename /ren     重命名文件/文件夹

ipconfig /all    获取ip地址 所在域    linux：ifconfig -a

Route print      路由信息

Arp -a        arp缓存

Netsh firewall show config  查看防火墙规则

Netsh firewall show state  

Netstat -an   获取端口信息

Whoami        当前用户权限

Hostname      主机名称

Set           环境变量

Query user    查看远程终端在线用户

Systeminfo    获取操作系统版本、类型、位数等相关信息、安装；

tasklist \svc

netstat -an | findstr "LISTENING"

· -b：      显示包含于常见每个链接或监听端口的可执行组件；

· -o：      显示与每个连接相关的所属进程ID；

· -v：       与b一起使用时将显示包含于为所有可执行组件创建连接或者监听端口的组件；

Netstat -anb  进程号、端口开放情况、开放端口程序、监听端口组件

Netsata -ano  tcp/udp协议信息、端口、进程号

Netstat -anvb 进程号、端口所用协议、调用的可执行组件、第三方进程的系统路径等

Tasklist /svc          获取运行的进程名称、服务、PID

Driverquery            查看已安装驱动程序列表

Net start              查看已经启动的windows服务

Msinfo32               获取更加详细的信息

Taskkill               是windows自带的终止进程程序

TASKKILL [/S system [/U username [/P [password]]]]{ [/FI filter] [/PID processid | /IM imagename] } [/T] [/F]

例如：taskkill /pid 452 /f        taskkill /im 360tray /f

用户管理命令：

Net user hack 123 /add  添加hack用户 密码为123

whoami             查询账号所属权限

whoami /all          查看sid值密码策略

net account         查看本地密码策略

net account /domain    查看域

netstat -an          网络连接查询

route print         路由打印

net user            查询本机用户列表

net session          查看当前会话

Net start           获取服务信息利用第三方漏洞提权、关闭杀毒软件、防火墙、以及关闭某些防护进程

Net stop servicesname   停止服务命

Net start servicename   开启服务命令

net share           查看SMB指向的

net view            查询同一域内机器列表

net view /domain      查询域列表

nltest /dclist:bk     查询域控主机名 nltest /dclist:域名

nltest /domain_trusts   列出域之间的信任关系

net view /domain:Secwing  查看Secwing域中的列表

net time /domain       判断主域，主域都做时间列表

net config workstation   当前登录域

net group "enterprise admins" /domain  企业管理组

net user /domain admin@126.com test 修改域用户密码(需要域管理员密码)

net user /domain       查询域用户

net group /domain       查询域里面的工作组

net group "domain admins" /domain  查询域管理员用户组

net localgroup administrators /domain  //登录本机的域管理员

net group "domain controllers" /domain  查看域控制器

mstsc /admin               远程桌面登录到console会话解决hash无法抓取问题

dsquery computer domainroot -limit 65535 && net group "domain computers" /domain   列出该域内所有机器名

dsquery user domainroot -limit 65535 && net user /domain  列出该域内所有用户名

dsqery subnet             列出该域内网段划分

dsqery group && net group /domain  //列出该域内分组

dsquery ou                列出该域内组织单位

dsquery server && net time /domain    列出该域内域控制器

net localgroup administrators  //查看本机管理员

Net localgroup adminnistrators hack /add   添加hack为管理员权限

Net localgroup adminnistrators    查看当前系统管理员

Net localgroup “remote desktop users” hack /add   加入远程桌面用户组

Net user hack     查看指定用户的信息

Net user guest /active:yes   激活guest用户

Net user guest 123



0x02：远程桌面开启指令

windows系统开启查询远程桌面（mstsc/rdesktop）

（1）XP/Win2k3/Win7/Win2k8/Win8.1/Win10/2012/2016（0：ON、1：OFF）：

                REG ADD "HKLM\SYSTEM\CurrentControlSet\Control\Terminal Server" /v fDenyTSConnections /t REG_DWORD /d 0 /f                                      

（2）Win2k3/Win7/Win2k8/Win8.1/Win10/2012/2016：（0：ON、1：OFF）：

                wmic RDTOGGLE WHERE ServerName='%COMPUTERNAME%' call SetAllowTSConnections 1         

（3）Winserver2008/2012/Win2k3/win7：

                wmic /namespace:\\root\cimv2\terminalservices path win32_terminalservicesetting where (__CLASS !="") call setallowtsconnections 1                                   

（4）Winserver2008/2012/：

                wmic /namespace:\\root\cimv2\terminalservices path win32_tsgeneralsetting where (TerminalName ='RDP-Tcp') call setuserauthenticationrequired 1                   

（5）XP/Win2k3/Win7/Win2k8/Win8.1/Win10/2012/2016（Metasploit）：

                meterpreter> run getgui -e

以下脚本或模块可以开启3389远程桌面端口、创建管理员账户密码、禁用远程桌面(TCP-In)防火墙入站规则。

                /usr/share/metasploit-framework/scripts/meterpreter/getgui.rb

                /usr/share/metasploit-framework/modules/post/windows/manage/enable_rdp.rb



0x03：常用端口及服务
数据库类端口：

MSSQL：       1433

Oracle：      1521

MYSQL：       3306

PostgreSQL:   5432

 

特殊服务类：

SSL(心脏滴血)：443

MS08067、MS110568、MS17010：445

Rsync(未授权)：873

CouchDB：      5984

redis(未授权)：6379

WebLogic(弱口令、反序列化)：7001/7002

memcache（未授权）：11211

Mongodb(未授权)：27017/27018

SAP(命令执行)：50000

hadoop(未授权)：50070、50030

 

远程连接端口：

ftp：   21

ssh：   22

telnet: 23

SMB(弱口令):445

路由(zebra)：2601/2604

远程桌面：3389 (0708)

