## 安装

实验室同学blog：

`https://blog.csdn.net/gzh_love_python/category_11351530.html`



## 非法指令问题：

大概率由于numpy版本错误，可尝试卸载numpy版本，安装低版本；jet46 numpy>=1.16



## 修改音频属性及声卡参数

```bash
# sox -V xx.wav -n    查看信息
# sox 2.wav -r 16000 2R.wav   修改采样率
# 复制一份wav文件保存audio_ok_name, 利用sox调整参数：通道-1 位-16 采样率-16k
# subprocess.call(["sox {} -r 16000 -b 16 -c 1 {}".format(audio_name, audio_ok_name)], shell=True)

# 使用aplay -l 查询声卡信息
# 使用amixer -c 声卡id  查询具体参数
# 使用amixer -c id set name 10 设置输出音量 
```



## Cmake 升级

**脚本安装**

适用于 JetPack 的底层系统是 Ubuntu 18.04 及以下的情况

```bash
# 卸载现有的 cmake
sudo apt remove --purge cmake

# 使用 Kitware 提供的预编译安装脚本来安装较新版本的 cmake
# 工作目录及临时变量准备
export cmake_latest=$(curl -s https://github.com/Kitware/CMake/releases/latest | grep -oE "\/tag\/v([[:digit:]]|\.)+" | grep -oE "([[:digit:]]|\.)+") && \
mkdir -p /tmp/cmake-${cmake_latest} && \
cd /tmp/cmake-${cmake_latest}

# 下载预编译脚本执行安装
wget -c https://github.com/Kitware/CMake/releases/download/v${cmake_latest}/cmake-${cmake_latest}-linux-aarch64.sh && \
chmod +x ./cmake-${cmake_latest}-linux-aarch64.sh && \
sudo ./cmake-${cmake_latest}-linux-aarch64.sh \
    --skip-license \
    --exclude-subdir \
    --prefix=/usr/local

# 安装后的清理工作
rm -rf /tmp/cmake-${cmake_latest}/ && \
unset cmake_latest

```

**编译安装**

```bash
mkdir -p ~/tools/
cd ~/tools/
wget https://github.com/Kitware/CMake/releases/download/v3.14.4/cmake-3.14.4.tar.gz
tar xvf cmake-3.14.4.tar.gz
cd cmake-3.14.4

# 未指定prefix会报错Could not find CMAKE_ROOT
./bootstrap --prefix=/usr

make
sudo make install

cmake --version
```



## Protobuf编译安装

下载https://github.com/protocolbuffers/protobuf/tree/v3.11.4

编译

```bash
cd 

./autogen.sh
./configure --prefix=/path

make 
make check
make install

protoc --version
```



## Jetson常用组件路径

/usr/src

/usr/local



## Jetson增加Swap

```bash
# 开启硬件性能模式
sudo nvpmodel -m 0 && sudo jetson_clocks
# 增加 DDR 可用空间，Xavier 默认内存为 16 GB，所以内存足够，如在 Nano 上尝试，请执行如下操作。
sudo fallocate -l 5G /var/swapfile
sudo chmod 600 /var/swapfile
sudo mkswap /var/swapfile
sudo swapon /var/swapfile
sudo bash -c 'echo "/var/swapfile swap swap defaults 0 0" >> /etc/fstab'
```



## SIM7600X 4G模块记录

### 硬件配置

\1. 串口拨码开关拨到U_TX,U_RX一侧,PWR跳冒连接D6（如果需要上电自动开机，PWR跳线帽接5V）
\2. 将4G模块接入Jetson Nano,再接入主天线,GNSS天线
\3. 上电开机,登录Jetson Nano,[登录教程点击查看](https://www.waveshare.net/study/portal.php?mod=view&aid=894).



### 软件配置

```bash
sudo apt-get install pyserial
wget -P ~/Documents/SIM7600X_4G_for_JETSON_NANO/ https://www.waveshare.net/w/upload/6/64/SIM7600X_4G_for_JETSON_NANO.tar.gz
cd ~/Documents/SIM7600X_4G_for_JETSON_NANO/
tar -xvf SIM7600X_4G_for_JETSON_NANO.tar.gz
sudo pip3 install Jetson.GPIO
wget -P ~/Documents/SIM7600X_4G_for_JETSON_NANO/ https://www.waveshare.net/w/upload/6/64/SIM7600X_4G_for_JETSON_NANO.tar.gz
cd ~/Documents/SIM7600X_4G_for_JETSON_NANO/
tar -xvf SIM7600X_4G_for_JETSON_NANO.tar.gz
sudo pip3 install Jetson.GPIO
```



### minicom调试

```bash
sudo minicom -D /dev/ttyUSB2 
crtl + a z e 
```



### 配置上网

**NDIS驱动上网**

```bash
# 强制设置为4G上网
AT+CNMP=38
# 查询网络质量
AT+CSQ
# 查询网络注册状
AT+CREG?
# 查询网络运营商
AT+COPS?
# 查询网络波段
AT+CPSI?
```

编译文件 make

```bash
# NDIS拨号上网
# root执行
insmod simcom_wwan.ko
lsmod
# 启动网口
ifconfig wwan0 up

# 拨号
minicom -D /dev/ttyUSB2
AT$QCRMCALL=1,1

# 分配ip
apt-get install udhcpc
udhcpc -i wwan0
ping -I wwan0 www.baidu.com

# RNDIS拨号上网
AT+CUSBPIDSWITCH=9011,1,1
# ifconfig 识别出usb1
sudo dhclient -v usb1
ping -I usb1 www.baidu.com
# 若不能上网
sudo route add -net 0.0.0.0 usb1
```



### 发送英文短信

```bash
AT+CMGF=1
AT+CSCS="GSM"
AT+CSCA?
AT+CSMP=17,167,0,240  # 240显示在终端，241保存在sim卡
AT+CMGS="18890...."
> MESSAGE CONTENT.
CTRL-Z # 发送
```



### 查看信息

```bash
AT+CMGL="ALL"
```



### 发送中文短信

```bash
AT+CMGF=1
AT+CSCS="UCS2"
AT+CSCA?
AT+CSMP=17,128,2,25
AT+CMGS="00310038003800390030003500370032003700300030"
> UCS2编码的消息内容，使用转换工具
> 5B8951685E3D6D4B8BD50074006500730074

CTRL-Z
```



## 安装VScode

https://code.visualstudio.com/Download下载arm64 deb

```bash
sudo dpkg -i download.deb
sudo apt install apt-transport-https
sudo apt update
sudo apt install code
code --version
```

