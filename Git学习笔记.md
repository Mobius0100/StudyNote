# Git使用

[Git Windows](http://msysgit.github.io/)

## 配置Git

每台电脑和每个github账户只需配一次

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
   
3. 创建本地仓库
   
   初始化本地文件夹并提交上传至github
   
   ```bash
   git init
   git add *
   git commit -m "first commit"
   git remote add origin git@github.com:yourName/yourRepo.git  # origin为远程库自定义名称
   git push -u 本地远程自定义名称 远程分支  # -u 表示将远程分支与本地分支合并，只需第一次提交时使用
   
   #由于远程库是空的，我们第一次推送master分支时，加上了-u参数，Git不但会把本地的master分支内容推送的远程新的master分支，还会把本地的master分支和远程的master分支关联起来，在以后的推送或者拉取时就可以简化命令。
   ```
   
   **删除远程地址**
   
   `git remote -v` 查看远程库信息
   
   `git remote rm origin`
   
4. 或者克隆远程仓库
   `git clone http://gitlab.cvhnu.tech/zouzhuo/ai-box`

## 添加文件并上传
1. `git add filename`  添加文件
2. `git commit -m "comment something"` 提交文件
2. `git diff` 查看变动 `git status ` 查看文件是否修改
2. `git log` 查看提交日志
3. `git push -u origin branch` 上传至主机origin的分支branch

## 修改
`git pull` 拉取远程仓库

`git branch -d name` 删除本地分支     -D强制删除

`git push origin -d name` 删除远程分支



## 使用分支

Git鼓励大量使用分支：

查看分支：`git branch`

创建分支：`git branch <name>`

切换分支：`git checkout <name>`或者`git switch <name>`

创建+切换分支：`git checkout -b <name>`或者`git switch -c <name>`

合并某分支到当前分支：`git merge <name>`

删除分支：`git branch -d/-D <name>`

禁用Fast Forword合并：`git merge --no-ff -m "xxx" <branchname>`

Bug分支：[Bug分支学习](https://www.liaoxuefeng.com/wiki/896043488029600/900388704535136)



## 标签管理

[标签管理](https://www.liaoxuefeng.com/wiki/896043488029600/902335479936480)

## 别名设置

```bash
git config --global alias.st status
git config --global alias.ci commit
git config --global alias.br branch
git config --global alias.last 'log -1'
git config --global alias.lg "log --color --graph --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(bold blue)<%an>%Creset' --abbrev-commit"
```



## 替换本地改动
假如你操作失误（当然，这最好永远不要发生），你可以使用如下命令替换掉本地改动:\
`git checkout -- filename`
此命令会使用 HEAD 中的最新内容替换掉你的工作目录中的文件。已添加到暂存区的改动以及新文件都不会受到影响。

假如你想丢弃你在本地的所有改动与提交，可以到服务器上获取最新的版本历史，并将你本地主分支指向它：\
`git fetch origin`\
`git reset --hard origin/master`

**如果出现本地与远程冲突导致无法push**，有两种办法：

1. 强覆盖
    `git push -f origin master`

2. 拉去再提交

    ```bash
    git pull --rebase origin master
    git push origin master
    ```

    

## 找回因失误导致本地文件丢失

```bash
git checkout -- filename # 恢复未提交的修改
git reflog
git reset --hard HEAD@{x}
```



## Macos 忽略./DS_Store

```bash
touch ~/.gitignore_global

---------
#Mac os
.DS_Store
**/.DS_Store
.DS_Store?
---------
git config --global core.excludesfile ~/.gitignore_global

#批量移除.DS_Store
find . -name .DS_Store -print0 | xargs -0 git rm -f --ignore-unmatch

```



