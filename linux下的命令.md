```
ysj 192.168.49.150
lyc 192.168.49.23
拷贝文件到远程机器：scp 路径/文件名 rd@192.168.49.23:路径
从远程机器拷贝文件到自己 scp rd@192.168.49.23:路径/文件名  路径
linux下常用命令：
1、rm -rf 删除文件夹及文件夹下的所有
2、rm -f 删除文件夹 rm 删除文件
3、df -h 查看磁盘使用量
4、ssh ysj@192.168.49.150  123qwe  /home/ysj/an_ts/util/db.cc
5、scp 路径/文件名 rd@192.168.49.23:路径
6、unzip 文件名 解压zip文件  
7、tar -xvf 文件名 解压tar.gz文件
8、运行idea 在安装目录bin/下运行   ./idea.sh
9、sudo apt-cache search 名称
10、sudo apt-get 名称
10、reboot 重启
11、sudo apt-get remove mysql-server
	sudo apt-get autoremove
	删除apt-get安装的软件
12、mvn compile 编译
13、file settings.xml
14、ls -al 查看隐藏文件  ll 查看文件显示drwxr-xr-x 
15、date 当前时间
16、sudo gedit /etc/maven/settings.xml 编辑器打开配置mvn <miror>和<localRepository>
17、whereis mvn       whereis java 
18、执行sql文件(test是数据库名字) mysql -uroot -p123456 test -e 'source /home/sunkai/project/springbootDemo/jeeplus.sql' 
19、配置idea环境变量  sudo vim /etc/profile 中加入PATH=$PATH:/home/sunkai/software/idea-IU-193.5662.53/bin
20、reboot 重启虚拟机
21、mysql启动  service mysql start
	mysql停止  service mysql stop
	mysql重启  service mysql restart
	查看mysql运行状态 systemctl status mysql.service
22、linux下mysql不支持自动区别大小写 需要在sudo vim /etc/mysql/my.cnf 下配置 [mysqld] lower_case_table_names = 1
23、出现lock锁问题，查看该apt命令的进程 例如ps -e | grep apt   然后执行sudo kill
```
```
安装常用软件
sudo apt-get install open-vm-tools
sudo apt-get install mysql-server
sudo apt-get install mysql-workbench
sudo apt-get install libmysqlclient-dev
sudo apt-get install openjdk-8-jdk
sudo apt-get install maven
sudo apt-get install git
```

```
unbuntu系统： 
1、查看网卡信息和名称 ip a
2、网卡配置文件  vi /etc/network/interface

修改Ubuntu默认apt下载源
默认下载源很慢，改成阿里的下载速度超快
sudo vim /etc/apt/sources.list 将文件内容替换成
deb http://mirrors.aliyun.com/ubuntu/ bionic main restricted universe multiverse
deb-src http://mirrors.aliyun.com/ubuntu/ bionic main restricted universe multiverse
deb http://mirrors.aliyun.com/ubuntu/ bionic-security main restricted universe multiverse
deb-src http://mirrors.aliyun.com/ubuntu/ bionic-security main restricted universe multiverse
deb http://mirrors.aliyun.com/ubuntu/ bionic-updates main restricted universe multiverse
deb-src http://mirrors.aliyun.com/ubuntu/ bionic-updates main restricted universe multiverse
deb http://mirrors.aliyun.com/ubuntu/ bionic-backports main restricted universe multiverse
deb-src http://mirrors.aliyun.com/ubuntu/ bionic-backports main restricted universe multiverse
deb http://mirrors.aliyun.com/ubuntu/ bionic-proposed main restricted universe multiverse
deb-src http://mirrors.aliyun.com/ubuntu/ bionic-proposed main restricted universe multiverse
更新
sudo apt-get update
sudo apt-get upgrade
```
```
压力测试：
打包项目分别在三个端口运行，使用Nginx负载均衡三个端口服务器
C:\Users\sunkai\Desktop\locks>java -jar locks-test-8080.jar --server.port=8080
C:\Users\sunkai\Desktop\locks>java -jar locks-test-8080.jar --server.port=8081
C:\Users\sunkai\Desktop\locks>java -jar locks-test-8080.jar --server.port=8082
用Apache进行多线程高并发下的压力测试
D:\ApacheJemter\Apache24\bin>ab -n 10000 -c 500 http://192.168.184.129/incr 
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
6、 docker rename <my_container> <my_new_container>  修改docker中服务的NAMES
7、 docker update 8a4 --restart=always 总是自动重启服务 8a4是服务ID
8、 systemctl restart docker 重启docker服务
9、 docker logs es1|grep mb  在es1的日志中查找mb
10、docker exec -it redis redis-cli 进入redis命令行

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
12.查看当前所在目录
pwd
13.查看elasticsearch日志
docker logs es1
```
