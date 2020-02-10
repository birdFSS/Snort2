- purpose:learn Snort and develop Snort
- author:birdFSS


### 一.快速设置
#### 1.参照install.md完成相关设置
#### 2.在主目录snort-2.x.xx使用下述命令进行测试
```c
mkdir log
sudo src/snort -dev -l ./log -c /etc/snort/snort.conf
```


#### 3.printf调试
snort-2.9.15.1/src/sfutil/acsmx2.c
snort-2.9.15.1/src/sfutil/bnfa_search.c
将这里面两个printf宏注释掉了，后面再改回来





