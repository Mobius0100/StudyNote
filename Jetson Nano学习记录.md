## 安装

实验室同学blog：

`https://blog.csdn.net/gzh_love_python/category_11351530.html`



## 非法指令问题：

大概率由于numpy版本错误，可尝试卸载numpy版本，安装低版本；jet46 numpy>=1.16



## 修改音频属性及声卡参数

```bash
# sox -V xx.wav -n
# 复制一份wav文件保存audio_ok_name, 利用sox调整参数：通道-1 位-16 采样率-16k
# subprocess.call(["sox {} -r 16000 -b 16 -c 1 {}".format(audio_name, audio_ok_name)], shell=True)

# 使用aplay -l 查询声卡信息
# 使用amixer -c 声卡id  查询具体参数
# 使用amixer -c id set name 10 设置输出音量 
```

=======
## 安装

实验室同学blog：

`https://blog.csdn.net/gzh_love_python/category_11351530.html`



## 非法指令问题：

大概率由于numpy版本错误，可尝试卸载numpy版本，安装低版本；jet46 numpy>=1.16



## 修改音频属性及声卡参数

```bash
# sox -V xx.wav -n
# 复制一份wav文件保存audio_ok_name, 利用sox调整参数：通道-1 位-16 采样率-16k
# subprocess.call(["sox {} -r 16000 -b 16 -c 1 {}".format(audio_name, audio_ok_name)], shell=True)

# 使用aplay -l 查询声卡信息
# 使用amixer -c 声卡id  查询具体参数
# 使用amixer -c id set name 10 设置输出音量 
```

