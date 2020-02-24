---
 title: Ubuntu

---

 ```linux
  apt-get update //更新软件库 
  apt-get upgrade //升级软件

  apt-get install ubuntu-desktop //安装Ubuntu桌面系统


 ```


    sudo vi /usr/share/lightdm/lightdm.conf.d/50-ubuntu.conf     //打开50-ubuntu.conf

    在末尾添加

        greeter-show-manual-login=true      //允许切换用户登陆
    
        allow-guest=false    //禁用Guest   

完整代码

    [Seat:*]
    user-session=ubuntu
    greeter-show-manual-login=true
    allow-guest=false

保存重启(在VI模式下编辑完成后使用Esc键切换到末行模式,然后输入:wq退出编辑)发现root用户登陆后还是有警告

修改/root/.profile文件 (图形界面下修改请勾选显示隐藏文件)
    
将mesg n 替换为 tty -s && mesg n

完整代码

 ~/.profile: executed by Bourne-compatible login shells.
if [ "$BASH" ]; then
if [ -f ~/.bashrc ]; then
. ~/.bashrc
fi
fi
tty -s && mesg n || true

保存后重启即可完美在桌面环境登陆root