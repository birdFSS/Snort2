# 安装流程

## 一.安装所需软件和库
### 1.1 直接安装
```c
sudo apt-get install gcc                 : 编译器,如果报错,apt-get install g++
sudo apt-get install flex                : DAQ所需的解析器
sudo apt-get install bison               : DAQ所需的解析器
sudo apt-get install zlib1g-dev          : Snort所需的压缩库
sudo apt-get install libpcap-dev         : Snort所需的网络流量捕获头文件库
sudo apt-get install libdnet-dev         : 不是必要的,只是snort为几个网络历程提供了简化的可移植接口
sudo apt-get install luajit              : lua的头文件库headers
sudo apt-get install liblua5.1-0-dev
sudo apt-get install liblua5.1-0-dev liblua50-dev liblualib50-dev
sudo apt-get install build-essential     : 提供编译软件的构建工具
sudo apt-get install libpcre3-dev        : Snort所需的pcre3的头文件
sudo apt-get install libdumbnet-dev      : 同libdnet
sudo apt-get install openssl libssl-dev  : ssl的加密组件,提供SHA和MD5文件签名
```

### 1.2下载源码安装
1. LuaJIT
```c
tar -zxvf LuaJIT-2.0.5.tar.gz
make && make install
```
2. pcre
```c
tar -zxvf pcre-x.xx.tar.gz
cd pcre-x.xx
./configure && make && make install
```

## 二.下载Snort源码
    首先在snort官网下载源代码。make install会用到sudo权限。
### 2.1 源码安装daq
```c
tar -zxvf daq-2.0.6.tar.gz
cd daq-2.0.6
./configure && make && make install
```
### 2.2 源码安装snort
```c
tar -xvzf snort-2.9.12.tar.gz
cd snort-2.9.12
./configure --enable-sourcefire
make
make install
```
### 2.3 创建相应的文件夹
1. Snort的安装目录
```c
sudo mkdir /etc/snort
sudo mkdir /etc/snort/rules
sudo mkdir /etc/snort/preproc_rules
sudo mkdir /usr/local/lib/snort_dynamicrules
sudo mkdir /etc/snort/so_rules
```
2. 存储过滤规则和服务器黑白名单
```c
sudo touch /etc/snort/rules/white_list.rules
sudo touch /etc/snort/rules/black_list.rules
sudo touch /etc/snort/rules/local.rules
```
3. 创建日志目录
```c
sudo mkdir /var/log/snort
sudo mkdir /var/log/snort/archived_logs
```
4. 调整权限
```c
sudo chmod -R 5775 /etc/snort
sudo chmod -R 5775 /var/log/snort
sudo chmod -R 5775 /var/log/snort/archived_logs
sudo chmod -R 5775 /etc/snort/so_rules
sudo chmod -R 5775 /usr/local/lib/snort_dynamicrules
```
5. 复制文件到指定目录
```c
cp snort-2.9.12/etc/*.conf* /etc/snort
cp snort-2.9.12/etc/*.map /etc/snort
cp snort-2.9.12/etc/*.dtd /etc/snort
cp snort-2.9.12/src/dynamic-preprocessors/build/usr/local/lib/snort_dynamicpreprocessor/* /usr/local/lib/snort_dynamicpreprocessor/            
```

6. 修改默认配置
```c
sudo vim /etc/snort/snort.conf
```

```c
snort.conf 
----------------------
#设置路径变量
var RULE_PATH /etc/snort/rules
var SO_RULE_PATH /etc/snort/so_rules
var PREPROC_RULE_PATH /etc/snort/preproc_rules

var WHITE_LIST_PATH /etc/snort/rules/
var BLACK_LIST_PATH /etc/snort/rules/

#将规则包含进来
include $RULE_PATH/local.rules
```

















