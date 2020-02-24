---
title: git的使用
date: 2019-11-12 20:32:48
tags:
---

##1.绑定用户
打开git-bash.exe（直接在桌面上点击右键，或者点击开始按钮找到Git Bash）
运行gitBash.gif

在打开的GIt Bash中输入以下命令（用户和邮箱为你github注册的账号和邮箱）

```
$ git config --global user.name "q0o0p-wow"
$ git config --global user.email "2825966877@qq.com"
```

##2.设置SSH key
先检查是否已生成密钥cd ~/.ssh，如果返回的ls有3个文件,则密钥已经生成。
如果没有密钥，执行如下命令：

```
$ ssh-keygen -t rsa -C "2825966877@qq.com"
```
![](1.png)

生成过程中一路按3次回车键就好了。第二次回车为设置密码（默认路径，默认没有密码登录）
生成成功后，去对应目录C:\Users\ASUS\ssh里面找公钥
  id_rsa 是私钥
  id_rsa.pub是公钥  
只需复制公钥即可。
接下来为github账号配置ssh key
切换到github，在右上角找到settings，然后打开SSH keys菜单， 点击Add SSH key新增密钥，填上标题（最好跟本地仓库保持一致）。

设置sshkey.gif
接着将id_rsa.pub文件中key粘贴到此，最后Add key生成密钥。

##3.建立本地仓库
cd 切换路径，打开blog（你的文件夹名）文件夹，执行命令：
```
git init
git add   //将所有文件添加到仓库
git commit -m "提交文件"  //双引号内是提交注释
```
初始化成功后你会发现项目里多了一个隐藏文件夹.git
```
ls -ah  //可用此命令查看
```

## 4.关联github仓库
```
git remote add origin https://github.com/q0o0p-wow/blog.git

```

---
# 合并分支
假如我们现在在dev分支上，刚开发完项目，执行了下列命令：
git  add .
git  commit -m '提交的备注信息'
git  push -u origin dev
想将dev分支合并到master分支，操作如下：

```
$ git checkout master //切换到master分支上
$ git pull origin master //远程仓库里的项目拉下来
$ git  merge dev
```
（如果是多人开发的话 需要把远程master上的代码pull下来）

删除文件：
```
git rm -r --cached 目标文件夹 
git commit -m '删除说明'
git push -u origin master //重新提交
```
---
# git分支的管理

```
$ git branch  //如果不加任何参数运行它，会得到当前所有分支的一个列表
$ git branch -r //查看远程分支
$ git checkout -b master origin/master //把远程分支master 拉取到本地
$ git checkout 分支名称  //切换分支
$ history  //查看历史
$ git status //查看要提交的条件
$ git add . //全部提交
$ git commit -m '注释'//提交注释
$ git push origin  本地分支名 ： 远程分支名  //上传本地当前分支代码到远程分支

$ git branch -m 原名 新  //改名
```

---
#git 仓库管理
```
git remote -v //远程仓库路径查询

git remote add origin <你的项目地址> //添加远程仓库，注:项目地址形式为https://gitee.com/xxx/xxx.git或者 git@gitee.com:xxx/xxx.git

git remote rm origin  //删除指定的远程

git push origin -d dev  //删除远程分支

git branch -d -r origin/dev  //只删除本地分支
git branch -d 名称  
```






参考：https://blog.csdn.net/weixin_41883384/article/details/80805580
