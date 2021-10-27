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

2. 网页端创建仓库
   
3. 创建本地仓库\
   `git init`\
   添加远程地址\
   `git remote add origin git@github.com:yourName/yourRepo.git`
   删除远程地址\
   `git remote rm origin`
4. 或者克隆远程仓库\
   `git clone http://gitlab.cvhnu.tech/zouzhuo/ai-box`

## 添加文件并上传
1. `git add filename`  添加文件
2. `git commit -m "comment something"` 提交文件
3. `git push -u origin branch` 上传至主机origin的分支branch

## 更新与合并
`git pull`

## 创建转换分支
`git checkout -b brancename`

## 替换本地改动
假如你操作失误（当然，这最好永远不要发生），你可以使用如下命令替换掉本地改动:\
`git checkout -- filename`
此命令会使用 HEAD 中的最新内容替换掉你的工作目录中的文件。已添加到暂存区的改动以及新文件都不会受到影响。

假如你想丢弃你在本地的所有改动与提交，可以到服务器上获取最新的版本历史，并将你本地主分支指向它：\
`git fetch origin`\
`git reset --hard origin/master`