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


















