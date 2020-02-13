centos7 安装php的redis扩展
下载地址
wget https://pecl.php.net/package/redis
解压
tar -zxvf redis-xxx
进入目录后
phpize
./configure --with-php-config=/usr/local/php/bin/php-config
make && make install