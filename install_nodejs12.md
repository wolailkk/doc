安装nodejs12的记录
安装方式采用源码安装
由于依赖的gcc版本过老升级了一下

centos升级g++7.3.0
依次执行如下步骤命令:

sudo yum install centos-release-scl
sudo yum install devtoolset-7

scl enable devtoolset-7 bash

