# Git使用

[Git Windows](http://msysgit.github.io/)

## 配置Git
1. 本地创建SSH Key\
`ssh-keygen -t rsa -b 2048 -C "your_email@youremail.com"` RSA算法\
`ssh-keygen -t ed25519 -C "<comment>"` ED25519算法

2. pub文件默认保存在用户目录\
在远程服务器(Github、Gitlab...etc)上配置SSH Keys\
将本地生成的pub文件内容拷贝至SSH Keys配置里

3. 验证是否配置成功
`ssh -T git@github.com` 

## 创建/克隆仓库
1. 配置username和email\
`git config --global user.name "your name"`\
`git config --global user.email "your_email@youremail.com"`

2. 创建本地仓库\
   `git init`\
   添加远程地址\
   `git remote add origin git@github.com:yourName/yourRepo.git`
3. 或者克隆远程仓库\
   `git clone http://gitlab.cvhnu.tech/zouzhuo/ai-box`
4. 

