# Web Server

本文记录构建一个web server的完整过程

### 项目启动

1、下载`git clone`：[agedcat/WebServer: Uubuntu 20 C++版本的web服务器 (github.com)](https://github.com/agedcat/WebServer)

2、编译`make`：[c++ make命令-掘金 (juejin.cn)](https://juejin.cn/s/c%2B%2B%20make%E5%91%BD%E4%BB%A4)

### 服务器端和客户端搭建

1、使用docker构建两个ubuntu容器，分别作为服务器端和客户端

`docker run -it image_name`

`docker attach container_name`

2、配置C++开发环境

`apt-get install git g++ gcc make`

3、运行服务器端，然后使用Webbench进行压力测试

server

`./bin/myserver`

client

`./webbench-1.5/webbench -c 100 -t 10 http://ip:port/`

查看ip：`cat /etc/hosts`，通常来说，这是的ip为`localhost(127.0.0.1)`、端口号为http的默认端口`80`