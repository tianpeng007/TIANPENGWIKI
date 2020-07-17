

# navicat错误码

## 1251错误码

 在本篇文章里小编给大家整理了一篇关于mysql与navicat建立连接出现1251错误怎么解决的技术文章，需要的朋友们参考下。
重装了电脑，安装了最新版的MySQL数据库，结果Navicat连接Mysql报1251错误，sqlyog报2058错误，但是window命令进入mysql，账号密码都是正确的。

在网上查的是，出现这个原因是mysql8之前的版本中加密规则是mysql_native_password，而在mysql8之后，加密规则是caching_sha2_password。
*解决问题方法有两种，  

一种是升级navicat驱动；   

一种是把mysql用户登录密码加密规则还原成mysql_native_password。  
我常用的是第二种方式：

```
ALTER USER 'root'@'%' IDENTIFIED BY 'password' PASSWORD EXPIRE NEVER; #更新一下用户的密码 


FLUSH PRIVILEGES; #刷新权限
```



```
docker run -p 3306:3306 --name mysql -v /opt/docker_v/mysql/conf:/etc/mysql/conf.d -e MYSQL_ROOT_PASSWORD=123456 -d imageID


```

我看好多人拿着命令直接复制，这样是不对的。
'root' 为你自己定义的用户名
'localhost' 指的是用户开放的IP，可以是'localhost'(仅本机访问，相当于127.0.0.1)，可以是具体的'*.*.*.*'(具体某一IP)，也可以是 '%' (所有IP均可访问)
'password' 是你想使用的用户密码