---
title: SpingCloud-OpenFeign远程调用
author: icesoda
date: 2023-01-12 09:07:38
tags:
 - 项目
 - Markdown
categories: 
  - [icesodaMall]
description:
---

## OpenFeign

> ​	Feign是一个声明式的HTTP客户端，它的目的就是让远程调用更加简单。Feign提供了HTTP请求的模板，**通过编写简单的接口和插入注解**，就可以定义好HTTP请求的参数、格式、地址等信息。
>
> ​	Feign整合了**Ribbon(负载均衡)**和**Hystrix(服务熔断)**可以让我们不再需要显式地使用这两个组件。
>
> ​	SpringCloudFeign在NetflixFeign的基础上扩展了对SpringMVC注解的支持，在其实现下，只需创建一个接口并用注解的方式来配置它，即可完成对服务提供方的接口绑定。简化了SpringCloudRibbon自行封装服务调用客户端的开发量。

- 引入依赖

  ![image-20230112094229204](https://icesoda-picgo.oss-cn-beijing.aliyuncs.com/imgtest/202301120943546.png)

- eg：member调用coupon服务

  ![image-20230112094857787](https://icesoda-picgo.oss-cn-beijing.aliyuncs.com/imgtest/202301120949104.png)

  ps：R代表 **ResultEntity**

### 想要远程调用别的服务

- 引入open-feign

- 编写一个接口，告诉SpringCloud这个接口需要调用远程服务

  1. 声明接口的每一个方法都是调用哪个远程服务的哪个请求

	![image-20230112095707363](https://icesoda-picgo.oss-cn-beijing.aliyuncs.com/imgtest/202301120957662.png)
	
- 开启远程调用功能 

  **@EnableFeignClients**

  ![image-20230112101033464](upload/image-20230112101033464.png)

- 测试（会员服务中远程调用优惠券）

  在会员服务的controller中调入优惠券远程接口

  ![image-20230112102151768](https://icesoda-picgo.oss-cn-beijing.aliyuncs.com/imgtest/202301121021256.png)

  远程获取结果：（被调用服务必须上线）

  ![image-20230112103808393](https://icesoda-picgo.oss-cn-beijing.aliyuncs.com/imgtest/202301121038255.png)

