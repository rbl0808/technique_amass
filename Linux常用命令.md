### 基本指令:

man:命令详细介绍
ls:显示所有文件
history：显示历史使用的命令
vim：打开vim编辑器
pwd：显示当前所在的目录
cd:切换当前工作目录
mkdir:创建目录
touch:创建文件
cp:复制文件
rm:移除 -r 表示递归移除; -f 表示无需确认强制删除

df:查看磁盘空间 #df -h -h 表示以可读性较高的形式展示大小
free:查看内存使用情况 #free -m 表示以mb为单位查看
head:查看文件的前n行，默认10行
tail:查看文件的末10行，默认10行
less:查看文件，以较少的内容输出展示，按q键退出
more:查看文件，以较多的内容输出展示，按q键退出
wc:统计文件内容信息 #wc -lwc l:lines行数 w:words单词数 c:bytes字节数
cal：显示日历
clear/command + l:清除终端中已经存在的命令和结果
|:管道符，
	作用：管道一般可以用于“过滤”，“特殊”，“扩展处理”。
	语法：管道不能单独使用，必须需要配合前面所讲的一些指令来一起使用，其作用主要是辅助作用。
	①过滤案例（100%使用）：需要通过管道查询出根目录下包含“y”字母的文档名称。

		#ls / | grep y
​		针对上面这个命令说明：
​		①以管道作为分界线，前面的命令有个输出，后面需要先输入，然后再过滤，最后再输出，通俗的讲就是管道前面的输出就是后面指令的输入；
​		②grep指令：主要用于过滤
​	②特殊用法案例：通过管道的操作方法来实现less的等价效果（了解）
​		之前通过less查看一个文件，可以#less 路径
​		现在通过管道还可以这么：#cat 路径|less
​	③扩展处理：请使用学过的命令，来统计某个目录下的文档的总个数？
​		答：#ls / | wc -l

### 高级指令:

​	hostname:操作服务器的主机名
​	id:查看一个用户的一些基本信息，默认当前用户
​	whoami:显示当前登录的用户名
​	ps:查看服务器进程信息 #ps -ef e:列出全部的进程 f:显示全字段
​	top:查看服务器的进程占的资源
​	find：查找文件
​	kill:杀死进程
​	ifconfig：操作网卡相关的指令
​	reboot:重新启动计算机
​	shutdown:关机
​	uptime:输出计算机的持续在线时间

### redis常用命令:

1.安装命令

````
brew install redis
````

2.启动Redis命令

````java
redis-server /usr/local/etc/redis.conf
````

3.停止redis server服务

````java
redis-cli shutdown
````

4.退出redis server服务

````java
Ctrl+c
````

5.测试redis server是否启动

````java
$ redis-cli ping 返回pong代表已经启动
````

6.启动redis客户端

````java
redis-cli 该命令会连接本地的Redis服务
````

### docker常用命令：

##### Redis:

```java
docker run -d --name docker-redis -p 6379:6379 redis:6.2.1
```

Mysql:

``````java
docker run -d --name docker-mysql -p 7777:3306 -e MYSQL_ROOT_PASSWORD=root mysql:8.0.23
``````

Zookeeper:

``````java
docker run -d --name dokcer-zookeeper -p 2181:2181 zookeeper:3.7.0
``````

进入容器：

````java
docker exec -it [contierId]
````

python打包:

``````
pythoninstaller -F timer.py
``````

mycat:

```
docker run --privileged=true -p 8066:8066 -p 9066:9066 --name docker-mycat -v /Users/rbl/document/docker/mycat/conf:/usr/local/mycat/conf -v /Users/rbl/document/docker/mycat/logs:/usr/local/mycat/logs  -d mycat:1.6.7.6
```

