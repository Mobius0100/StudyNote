# Jetson nano USB声卡调试
1. 检查是否有USB声卡设备
``` lsusb ```
2. 查看声卡设备信息
``` aplay -l ```
3. 查看usb声卡控制参数
``` amixer -c cardid ```
4. 调节音量大小
``` amixer -c cardid set cardname xx%|xx ```
5. 播放音频文件
``` aplay xxx.wav ```
6. pactl命令



# 修改音频文件属性

使用 sox 查看音频属性：```sox -V xx.wav -n```

修改属性：复制一份wav文件保存audio_ok_name, 利用sox调整参数--通道-1 位-16 采样率-16k

```subprocess.call(["sox {} -r 16000 -b 16 -c 1 {}".format(audio_name, audio_ok_name)], shell=True)```

`sox audioname -r 48000 -b 16 -c 1 outfilename`



# 查看启动服务

```bash
sudo lsof | grep /dev/tty*           # 列出串口占用程序
sudo systemctl list-unit-files | grep enabled   #列出允许开机自启 
sudo systemctl disable nginx.service # 禁止开机启动
sudo systemctl stop nginx.service    # 停止服务
```

<img src="picture/LinuxUsbControl/watermark,type_ZHJvaWRzYW5zZmFsbGJhY2s,shadow_50,text_Q1NETiBA5bCP55m944CB55G2,size_20,color_FFFFFF,t_70,g_se,x_16.png" alt="服务管理"  />



# APT错误

```bash
sudo apt-get clean
sudo apt-get update && sudo apt-get upgrade

sudo dpkg --configure -a
sudo apt-get -f install
```



# Ubuntu图形化界面问题

**问题1：**进入LDXE界面黑屏，需要输入密码，可以进入登录界面，**通过更改图形界面解决**

**问题2：**同上，但因不需要输入密码，不能进入登录界面，**通过更改显示管理器解决**

======但图形界面和登录界面无法工作的原因未知======



所有图形化会话位置：/usr/share/xsessions

显示管理器：DM(display manager)

简单来说， 显示管理器 (display manager) （DM）是一个为你的Linux发行版提供**图形登录功能**的程序。它控制用户会话并管理用户认证。显示管理器会在你输入用户名和密码后，立即启动显示服务器并加载桌面环境。

我们平时打开linux时的那个登录界面，就是显示管理器。gdm3就是gnome桌面环境使用的显示管理器，同样KDE使用的是sddm。开启linux时会先启动并进入显示管理器，也就是用户登录界面。然后我们在其中输入用户名和密码，就进入了桌面环境。

```bash
sudo apt install lightdm lightdm-gtk-greeter-settings  # 安装lightdm
sudo dpkg-reconfigure lightdm # 配置默认显示管理器
cat /etc/X11/default-display-manager # 查看默认显示管理器
```

