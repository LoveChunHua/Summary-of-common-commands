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
```