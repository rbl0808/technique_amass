1. ### k8s在企业中的应用场景 

   - 自动化运维平台
   - 充分利用服务器资源
   - 服务无缝迁移

2. ### 服务部署模式变化

   - 物理机部署
   - 虚拟机部署
   - 容器化

3. ### 部署方式变化带来的影响

   SOA架构，微服务架构

   - 虚拟机服务部署。openstack
   - 容器化部署模式。k8s
     - 服务如何横向扩展
     - 容器宕机怎么办，如何恢复数据
     - 版本如何迭代，如何更新不影响现有业务
     - 如何监控容器
     - 如何调度创建容器
     - 数据安全性如何保证

4. ### 云架构

   云 使用容器构建的一套服务集群网络，k8s管理云中的容器

   - iaas  基础设施及服务

     ​    用户租用云主机，不需要考虑网络、DNS、存储、硬件环境方面的问题

        运营商 提供网络、存储、DNS，这样服务就叫基础设施服务

   - paas 平台及服务  MYSQL/ES/MQ/。。。

   - saas 钉钉  。。。

   - serverless  云服务器，使用公有云或者私有云环境

5. ### 云原生

   - 为了让应用程序都与运行在云上的解决方案，这样方案叫做云原生
     1. 容器化
     2. 微服务
     3. CI/CD. 持续集成交付
     4. DevOps

6. ### k8s 架构原理

   1. goole公司使用Go语言开发，borg系统

   2. 架构

      1. master节点

         - api server。k8s网关，所有的指令请求都必须经过api server
         - Scheduler  调度器,使用调度算法,把请求资源调度某一个node节点
         - Controller 控制器,维护k8s资源对象
         - etcd 存储资源对象

      2. node节点

         - Docker 运行容器的基础环境
         - Kubelet 在每一个node节点都存在一份,在node节点上的资源操作指令由kubelet执行
         - kube-proxy 代理服务,负载均衡
         - fluentd 日志收集服务
         - pod 是k8s管理的基本单元,pod是内部容器。k8s不直接管理容器,而是管理pod

         关系:一个master对应一群node节点

         ![](https://images2018.cnblogs.com/blog/1411267/201807/1411267-20180708171415257-822334387.jpg)





7. ### pod

8. ### ReplicaSet副本控制器

   - ReplicationController副本控制器

   - ReplicaSet副本控制器

     控制pod副本的数量,永远与预期设定的数量保持一致，如果有服务宕机，自动创建新的Pod，保证数量一致

   两种控制器的区别

   1. ReplicaSet 可以单选也可以复合选择
   2. ReplicationController只能单选

9. ### Deployment 部署对象

   1. 服务部署结构模型

   2. 滚动更新

      ReplicaSet不支持滚动更新，Deployment支持，通常两者一起使用

      Deployment创建新的RS，RS建立新的Pod并维护删除旧的RS

      #### Deployment管理RS，RS管理Pod

10. ### StatefulSet部署对象

    1. 跟Deployment类似，部署有状态的服务容器,比如Mysql等有实时数据需求的pod，常以pvx或文件系统作为辅助
    
11. ### service VIP深入原理

    1. service和pod都是进程,也不能对外网提供服务
    2. sercie通过(iptables或者ipvs)做数据包分发
    3. service和pod可以通信,局域网通信

12. ### service和pod如何关联

    1. 标签选择器

       ​		![](/Users/rbl/Desktop/截图/k8s.png)

       

