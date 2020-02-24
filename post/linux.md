---
title: Linux 基础篇(ubuntu19.04)
---

---
换yum
```linux
sudo cp /etc/apt/sources.list /etc/apt/sources_init.list  //备份原来的源
sudo gedit /etc/apt/sources.list  //更换源
```


阿里源：
```linux
deb http://mirrors.aliyun.com/ubuntu/ xenial main
deb-src http://mirrors.aliyun.com/ubuntu/ xenial main

deb http://mirrors.aliyun.com/ubuntu/ xenial-updates main
deb-src http://mirrors.aliyun.com/ubuntu/ xenial-updates main

deb http://mirrors.aliyun.com/ubuntu/ xenial universe
deb-src http://mirrors.aliyun.com/ubuntu/ xenial universe
deb http://mirrors.aliyun.com/ubuntu/ xenial-updates universe
deb-src http://mirrors.aliyun.com/ubuntu/ xenial-updates universe

deb http://mirrors.aliyun.com/ubuntu/ xenial-security main
deb-src http://mirrors.aliyun.com/ubuntu/ xenial-security main
deb http://mirrors.aliyun.com/ubuntu/ xenial-security universe
deb-src http://mirrors.aliyun.com/ubuntu/ xenial-security universe
```

---
网易源：
```linux
deb http://mirrors.163.com/ubuntu/ wily main restricted universe multiverse
deb http://mirrors.163.com/ubuntu/ wily-security main restricted universe multiverse
deb http://mirrors.163.com/ubuntu/ wily-updates main restricted universe multiverse
deb http://mirrors.163.com/ubuntu/ wily-proposed main restricted universe multiverse
deb http://mirrors.163.com/ubuntu/ wily-backports main restricted universe multiverse
deb-src http://mirrors.163.com/ubuntu/ wily main restricted universe multiverse
deb-src http://mirrors.163.com/ubuntu/ wily-security main restricted universe multiverse
deb-src http://mirrors.163.com/ubuntu/ wily-updates main restricted universe multiverse
deb-src http://mirrors.163.com/ubuntu/ wily-proposed main restricted universe multiverse
deb-src http://mirrors.163.com/ubuntu/ wily-backports main restricted universe multiverse
```

---

## 更新：

```Linux
 sudo apt-get update    //  <!-- wget install -y update -->  更新源

 sudo apt-get -f install //   卸载出错的包，重新安装正确版本的

 sudo apt-get upgrade //  <!-- wegt install -y upgrade --> 更新软件

```


## 查找文件所在位置

　　1.whereis 文件名

　　特点:快速,但是是模糊查找,例如 找 #whereis mysql 它会把mysql,mysql.ini,mysql.*所在的目录都找出来.

　　2.find / -name 文件名

　　特点:准确,但速度慢,消耗资源大,例如我想找到php.ini的准确位置,就需要用

　　#find / -name php.ini

　　3.locate 文件名

　　强力推荐的方法,最快,最好的方法.