```
unbuntu系统： 
1、查看网卡信息和名称 ip a
2、网卡配置文件  vi /etc/network/interface
```

```
CentOs系统：
1、查看ip地址                 ifconfig -a //ens33网卡名称 -a可选     192.168.184.129
2、查看网关                   netstat -rn    192.168.184.2
3、root权限                   su    然后输入SunKai123456
4、重启docker                 systemctl restart docker
5、关闭docker                 systemctl stop docker
6、zoolytic连接zookeeper      输入zookeeper ip地址：端口号   192.168.184.129：2181
7、列出进程                   ps   
8、关闭进程                   kill -9 [进程id]

1、 docker ps 查看正在运行的 -a可选 详细一些
2、 docker rm [CONTAINER ID] 删除之前未退出的docker容器
3、 docker run --name zookeeper --restart always -d zookeeper 
4、 service docker status 查看状态
5、 docker restart f57  重启服务，f57是服务的CONTAINER ID 前三位

Docker下使用zookeeper镜像
1.查询zookeeper
docker search zookeeper
2.拉取zookeeper
docker pull zookeeper
或
docker pull jplock/zookeeper:3.4.10
3.查看镜像
docker images
或
docker image ls
4.启动zookeeper容器
docker run --name zookeeper --restart always -d zookeeper:3.4.10
或
docker run -t --name zookeeper1 --restart always -d zookeeper:3.4.10
5.查看容器
docker ps -a
6.查看容器实例进程信息
docker top 实例别名
docker top zookeeper
或
docker top 容器ID
docker top xxxx
或
ps -ef | grep zookeeper
7.停止zookeeper实例进程
docker stop zookeeper
8.启动实例
docker start zookeeper
9.重启实例
docker restart zookeeper
10.查看zookeeper进程日志
docker logs -f zookeeper
11.使用zookeeper命令行客户端连接zookeeper
docker exec -it 容器名称 /bin/bash
```