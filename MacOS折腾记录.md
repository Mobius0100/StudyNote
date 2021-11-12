# MacOS记录
## Homebrew安装
安装
`/usr/bin/ruby -e "$(curl -fsSL https://cdn.jsdelivr.net/gh/ineo6/homebrew-install/install)"`
速度慢解决办法

```bash
cd "$(brew --repo)/Library/Taps/"
mkdir homebrew && cd homebrew
git clone git://mirrors.ustc.edu.cn/homebrew-core.git
```



## MQTT服务器搭建

### 安装mosquitto

```bash
brew install mosquitto
```

### 配置文件

默认路径在/usr/local/etc/mosquitto/mosquitto.conf

**修改端口，账户：**

在conf文件中添加：

1. allow_anonymous false   # 禁止匿名登录，则需配置账号
2. port 1883
3. port 1884

**配置账号：**

1. `touch /etc/mosiquitto/pwfile`
2. `mosquitto_passwd /etc/mosiquitto/pwfile`  #输入命令后设置密码

### 用法

**开启与关闭服务:**

```bash
brew services start mosquitto
brew services stop mosquitto
brew services restart mosquitto
mosquitto -c /etc/mosquitto/mosquitto.conf -d   #以特定配置文件启动，-d表示后台
```

**测试：**

订阅与发布：

`mosquitto_sub/mosquitto_pub`

常用参数：

| 参数 |    描述    |
| :--: | :--------: |
|  -h  | 服务器主机 |
|  -t  | 指定topic  |
|  -u  |   用户名   |
|  -P  |    密码    |
|  -i  |  客户端id  |
|  -m  | 发布的内容 |

`mosquitto_sub -h localhost -t "test/#" -u hanmeimei -P 123456 -i "client1"`

`mosquitto_pub -h localhost -t "test/abc" -u lilei -P 123456 -i "client3" -m "How are you?"`

