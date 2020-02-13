wget https://github.com/swoole/swoole-src/archive/v4.4.15.tar.gz
tar -zxvf v4.4.15.tar.gz
phpize  //不操作这一步不会发现./configure
yum install autoconf
yum install glibc-headers
yum install gcc-c++ 
make && make install

php --ini查看配置文件地址
php -m 查看是否成功安装扩展
//最后一行插入
extension=swoole.so