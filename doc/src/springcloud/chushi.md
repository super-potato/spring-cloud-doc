#初识spring cloud
##什么是Spring Boot
Spring Boot简化了基于Spring的应用开发，通过少量的代码就能创建一个独立的、产品级别的Spring应用。 Spring Boot为Spring平台及第三方库提供开箱即用的设置，这样你就可以有条不紊地开始。多数Spring Boot应用只需要很少的Spring配置。
Spring Boot是由Pivotal团队提供的全新框架，其设计目的是用来简化新Spring应用的初始搭建以及开发过程。该框架使用了特定的方式来进行配置，从而使开发人员不再需要定义样板化的配置。用我的话来理解，就是Spring Boot其实不是什么新的框架，它默认配置了很多框架的使用方式，就像maven整合了所有的jar包，Spring Boot整合了所有的框架（不知道这样比喻是否合适）。

[更多介绍](http://blog.csdn.net/qq_31655965/article/details/71258191)

[springboot学习资料汇总](http://www.ityouknow.com/springboot/2015/12/30/springboot-collect.html)
##什么是Spring Cloud
Spring Cloud是一系列框架的有序集合。它利用Spring Boot的开发便利性巧妙地简化了分布式系统基础设施的开发，如服务发现注册、配置中心、消息总线、负载均衡、断路器、数据监控等，都可以用Spring Boot的开发风格做到一键启动和部署。Spring并没有重复制造轮子，它只是将目前各家公司开发的比较成熟、经得起实际考验的服务框架组合起来，通过Spring Boot风格进行再封装屏蔽掉了复杂的配置和实现原理，最终给开发者留出了一套简单易懂、易部署和易维护的分布式系统开发工具包。
微服务是可以独立部署、水平扩展、独立访问（或者有独立的数据库）的服务单元，Spring Cloud就是这些微服务的大管家，采用了微服务这种架构之后，项目的数量会非常多，Spring Cloud做为大管家就需要提供各种方案来维护整个生态。
Spring Cloud就是一套分布式服务治理的框架，既然它是一套服务治理的框架，那么它本身不会提供具体功能性的操作，更专注于服务之间的通讯、熔断、监控等

[springcloud学习资料汇总](http://www.ityouknow.com/springcloud/2016/12/30/springcloud-collect.html)
##为什么选择使用spring cloud
1. 随着项目的发展和业务的增加，单体应用面对的业务需求更加广泛，不断扩大的需求使得单体应用变的越来越臃肿。
2. 作为一个新手，准备实施微服务框架时，为了避免前辈踩过的坑，在一些核心问题的解决方案上，我们的选择多之又多，这必然会导致在做技术选型的初期，需要花费巨大的时间调研，分析与实验精力
3. Spring Cloud整合了来自不同公司或组织的诸多开源框架。它不仅是解决微服务中的某一个问题，而是一个解决微服务架构实施的综合性解决框架。
4. Spring Cloud具有非常强大的技术后盾Spring，具有非常活跃的技术社区，频繁的优化和更新。

##spring cloud目前国内使用情况
1. 中国联通子公司 http://flp.baidu.com/feedland/video/?entry=box_searchbox_feed&id=144115189637730162&from=timeline&isappinstalled=0
2. 上海米么金服
3. 指点无限（北京）科技有限公司
4. 易保软件 目前在定制开发中http://www.ebaotech.com/cn/
5. 广州简法网络
6. 深圳睿云智合科技有限公司 持续交付产品基于Spring Cloud研发 http://www.wise2c.com
7. 猪八戒网，目前调研中
8. 上海云首科技有限公司
9. 华为 整合netty进来用rpc 包括nerflix那套东西 需要注意的是sleuth traceid的传递需要自己写。tps在物理机上能突破20w
10. 东软
11. 南京云帐房网络科技有限公司
12. 四众互联(北京)网络科技有限公司
13. 深圳摩令技术科技有限公司
14. 广州万表网
15. 视觉中国
16. 上海秦苍信息科技有限公司-买单侠
17. 爱油科技(大连)有限公司 爱油科技基于SpringCloud的微服务实践
18. 广发银行
19. 卖货郎(http://www.51mhl.com/）
20. 拍拍贷
21. 甘肃电信
22. 新浪商品部
23. 春秋航空
24. 冰鉴科技
25. 万达网络科技集团-共享商业平台-共享供应链中心
26. 网易乐得技术团队
27. 饿了么某技术团队
28. 高阳捷迅信息科技–话费中心业务平台–凭证查询及收单系统

##组件及功能介绍
####spring-boot-actuator
> actuator是springboot中一个用来做系统健康检测的一个模块，它提供一个resetful的api接口，可以将系统运行过程中的磁盘空间、线程数、以及程序连接的数据库情况通过json返回，然后再结合预警、监控模块进行实时系统监控。
- 功能：

  | HTTP方法 | 路径              | 描述            | 鉴权    |
  | ------ | --------------- | ------------- | ----- |
  | GET    | /autoconfig     | 查看自动配置的使用情况   | true  |
  | GET    | /configprops    | 查看配置属性，包括默认配置 | true  |
  | GET    | /beans          | 查看bean及其关系列表  | true  |
  | GET    | /dump           | 打印线程栈         | true  |
  | GET    | /env            | 查看所有环境变量      | true  |
  | GET    | /env/{name}     | 查看具体变量值       | true  |
  | GET    | /health         | 查看应用健康指标      | false |
  | GET    | /info           | 查看应用信息        | false |
  | GET    | /mappings       | 查看所有url映射     | true  |
  | GET    | /metrics        | 查看应用基本指标      | true  |
  | GET    | /metrics/{name} | 查看具体指标        | true  |
  | POST   | /shutdown       | 关闭应用          | true  |
  | GET    | /trace          | 查看基本追踪信息      | true  |

  ​


[spring-boot-actuator 学习](http://blog.csdn.net/minicto/article/details/54951247)
####spring-cloud-netfix
#####spring-cloud-eureka
> 云端服务发现，一个基于 REST 的服务，用于定位服务，以实现云端中间层服务发现和故障转移。


- **服务注册** 每个服务单元向注册中心登记自己提供的服务，将主机与端口号，版本号，通讯协议等一些附加信息告知注册中心，注册中心按服务名分类组织服务清单。另外，服务中心还需要以心跳的方式去检测清单中的服务是否可用，如不可用，需要从服务清单中删除，达到删除故障服务的效果。

- **服务发现** 由于在服务治理下运作，服务间的调用不再采用通过具体的实例地址来实现，而是通过向服务服务名发起请求调用实现（ribbon）,服务注册中心返回服务名对应的所有的实例清单。

![image](https://raw.githubusercontent.com/super-potato/tupian/master/iad_design/eureka1.png)
#####spring-cloud-zuul
> Zuul 是在云平台上提供动态路由,监控,弹性,安全等边缘服务的框架。Zuul 相当于是设备和 Netflix 流应用的 Web 网站后端所有请求的前门。


#####spring-cloud-ribbon
> 提供云端负载均衡，有多种负载均衡策略可供选择，可配合服务发现和断路器使用。

通过RestTemplate实现面向服务接口的调用。支持**GET**,**POST**,**PUT**,**DELETE**

- 负载均衡策略
  - RandomRule  从实例列表随机选取。选择逻辑在一个while(server == null)循环之内，正常情况下都应该选出一个服务示例，如果出现死循环获取不到服务实例，则有可能存在并发的Bug

  - RoundRobinRule（默认） 按照线性轮循一次选择每个实例。随机次数超过十次，结束尝试

  - RetryRule 内部还定义了一个IRule，默认RoundRobinRule。在指定时间内反复尝试，超时返回null

  - weightedResponseTimeRule 基于RoundRobinRule增加了根据实例的运行情况来计算权重，然后根据权重挑选实例。主要有三个核心内容：

    - 定时任务

      - 每30s执行一次权重计算
    - 权重计算

      - 记录每个实例的统计信息，累加所有实例的平均响应时间，得到总平均响应时间totalResponseTime
      - 循环所有的实例计算其权重，weightSoFar+=totalResponseTime - 实例平均响应时间，其中weightSoFar初始化值为0。每个实例权重结果保存到ArrayList currentWeights中。
    - 实例选择
      - 判断最后一个实例的权重是否< 0.001d，若小于，采用RoundRobinRule策略
      - 生成一个[0,最大权重值)区间内的随机数。
      - 遍历权重清单currentWeights，若权重大于等于随机的得到的数值，就选择这个实例


- 其他 

#####spring-cloud-Feign
> Feign是一种声明式、模板化的HTTP客户端。

Spring Cloud Feign 在RestTemplate的基础上作了进一步的封装，由它来帮助我们定义和实现依赖服务接口的定义。我们只需要创建一个接口并用注解的方式来配置它。
#####spring-cloud-hystrix
> 熔断器，容错管理工具，旨在通过熔断机制控制服务和第三方库的节点,从而对延迟和故障提供更强大的容错能力。

在分布式架构中，当某个服务单元发生故障（类似电器发生短路）之后，通过断路器的故障监控（类似熔断保险丝）， 想调用方返回一个错误响应，而不是长时间等待，这样就不会使得线程因调用故障服务被长时间占用不放，避免了故障在分布式系统中的蔓延
针对这一机制，Spring Cloud Hystrix实现了断路器，线程隔离等一系列服务保护功能。它也是基于Netfix的开源框架Hystrix实现的，该框架的目标在于通过控制那些访问远程系统、服务和第三方库的节点，从而对延迟和故障提供更强大的容错能力。

​	Hystrix具备：

- 服务降级
- 服务熔断
- 线程和信号隔离
- 请求缓存
- 请求合并
- 服务监控
- 集群监控（Turbine）



####spring-cloud-task
> 提供云端计划任务管理、任务调度。


####spring-cloud-bus
> 事件、消息总线，用于在集群（例如，配置变化事件）中传播状态变化，可与Spring Cloud Config联合实现热部署。
####spring-cloud-sleuth
> 日志收集工具包，封装了Dapper和log-based追踪以及Zipkin和HTrace操作，为SpringCloud应用实现了一种分布式追踪解决方案。
####spring-cloud-stream
> 数据流操作开发包，封装了与Redis,Rabbit、Kafka等发送接收消息。
####spring-cloud-zookeeper
####spring-cloud-starters
####spring-cloud-CLI




##我们目前的架构
##我们将来的架构

![](test.jpg)
![](https://github.com/super-potato/tupian/tree/master/dhxy/008.jpg)

![](http://upload-images.jianshu.io/upload_images/259-0ad0d0bfc1c608b6.jpg?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

















