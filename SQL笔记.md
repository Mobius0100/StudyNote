# 安装

```bash
apt-get install mysql-server  # Linux
brew install mysql # Macos
https://dev.mysql.com/downloads/mysql/  # windows下载安装
```



# 运行

```bash
mysql -uroot -p # mysql -u username -p password
->password

```



# 用户权限

创建用户--->赋予权限--->撤销权限--->显示权限--->删除用户--->修改密码

```sql
CREATE USER 'joytom'@'%' IDENTIFIED BY '123321';  # ‘username’@‘host’ %为任意ip
grant select,update on copytest.student to "joytom"@'%'; #grant 权限 all on 数据库 *.* to
revoke .... on *.* to ...;
show grants for 'user'@'%';
drop user 'joytom'@'%';
select user,host from mysql.user;
SET PASSWORD FOR 'joytom'@'%' = PASSWORD('123123');
```



# 开启远程连接

```bash
sudo netstat -tap | grep mysql # 是否安装成功
sudo vim /etc/mysql/mysql.conf.d/mysqld.cnf  #找到mysql配置文件
# bind-address = 127.0.0.1  注释该行
sudo /etc/init.d/mysql restart # 重启mysql
netstat -nlt | grep 3306 # 查看3306端口是否变为0.0.0.0
```

