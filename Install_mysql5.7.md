安装mysql5.7
一、安装YUM Repo
1、由于CentOS 的yum源中没有mysql，需要到mysql的官网下载yum repo配置文件。
下载命令：

wget https://dev.mysql.com/get/mysql57-community-release-el7-9.noarch.rpm

2、然后进行repo的安装：
rpm -ivh mysql57-community-release-el7-9.noarch.rpm

执行完成后会在/etc/yum.repos.d/目录下生成两个repo文件mysql-community.repo mysql-community-source.repo


二、使用yum命令即可完成安装
注意：必须进入到 /etc/yum.repos.d/目录后再执行以下脚本

1、安装命令：
yum install mysql-server

2、启动msyql：
systemctl start mysqld #启动MySQL

3、获取安装时的临时密码（在第一次登录时就是用这个密码）：
grep 'temporary password' /var/log/mysqld.log

4、倘若没有获取临时密码，则
4.1、删除原来安装过的mysql残留的数据

rm -rf /var/lib/mysql

4.2.再启动mysql

systemctl start mysqld #启动MySQL

三、登录：
1、方式一（已验证）：
mysql -u root -p

然后输入密码（刚刚获取的临时密码）

2、方式二（未验证）：
进入mysql数据库

root@test:/home# mysql -uroot -proot   <uroot是用户名，proot是密码>

如：

root@test:/home# mysql -root -XXXX

3、若登录不了，则进行以下配置，跳过登录验证
3.1、重置密码的第一步就是跳过MySQL的密码认证过程，方法如下：

3.2、vim /etc/my.cnf(注：windows下修改的是my.ini)

在文档内搜索mysqld定位到[mysqld]文本段：

/mysqld(在vim编辑状态下直接输入该命令可搜索文本内容)

在[mysqld]后面任意一行添加“skip-grant-tables”用来跳过密码验证的过程


3.3、保存文档并退出：

#:wq

六、开启远程控制
MySQL默认是没有开启远程控制的，必须添加远程访问的用户，即默认是只能自己访问，别的机器是访问不了的。

1、方式一（已验证）：
　   1.1、连接服务器: mysql -u root -p

　　1.2、看当前所有数据库：show databases;

　　1.3、进入mysql数据库：use mysql;

　　1.4、查看mysql数据库中所有的表：show tables;

　　1.5、查看user表中的数据：select Host, User,Password from user;

　　1.6、修改user表中的Host:   update user set Host='%' where User='root';  

                说明： % 代表任意的客户端,可替换成具体IP地址。

　　1.7、最后刷新一下：flush privileges;

https://blog.csdn.net/wohiusdashi/article/details/89358071