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

