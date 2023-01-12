---
title: Nacos配置中心
categories:
  - []
tags: []
author: icesoda
date: 2023-01-12 10:44:31
cover:
description:

---

## 简单示例

>    如何使用nacos作为配置中心 统一管理配置
>    1. 引入依赖
>       `<dependency>
>           <groupId>com.alibaba.cloud</groupId>
>           <artifactId>spring-cloud-starter-alibaba-nacos-discovery</artifactId>
>       </dependency>`
>   
>    2. 创建一个 bootstrap.properties
>       `spring.application.name=icesodamall-coupon
>       spring.cloud.nacos.config.server-addr=127.0.0.1:8848`
>   
>    3. 需要给配置中心默认添加一个叫 数据集(Data Id)
>
>          默认规则当前应用名
>
>          `.properties(icesodamall-coupon.properties)`
>
>    4. 给应用名.properties添加任何配置
>
>    5. 动态获取配置
>
> @RefreshScope: 动态获取并刷新配置
> @Value("${配置项的名}")： 获取到配置。
> 如果配置中心和当前应用的配置文件照片那个都配置了相同的项 优先使用配置中心的配置

- 在公共项目中导入注册发现的依赖

  ![image-20230112145924335](https://icesoda-picgo.oss-cn-beijing.aliyuncs.com/imgtest/202301121459478.png)

- 创建文件，bootstrap.properties 会优先于 application.properties

  ![image-20230112150110809](https://icesoda-picgo.oss-cn-beijing.aliyuncs.com/imgtest/202301121508354.png)

  ![image-20230112150536716](https://icesoda-picgo.oss-cn-beijing.aliyuncs.com/imgtest/202301121509098.png)

- 测试

  ![image-20230112150707186](https://icesoda-picgo.oss-cn-beijing.aliyuncs.com/imgtest/202301121508921.png) 
1. 添加配置文件信息
  ![image-20230112150811664](https://icesoda-picgo.oss-cn-beijing.aliyuncs.com/imgtest/202301121542548.png)

  ![image-20230112154234380](https://icesoda-picgo.oss-cn-beijing.aliyuncs.com/imgtest/202301121542563.png)

2. 结果：

![image-20230112151502640](https://icesoda-picgo.oss-cn-beijing.aliyuncs.com/imgtest/202301121548636.png)

3. 若需修改，just:
   ![image-20230112154646252](https://icesoda-picgo.oss-cn-beijing.aliyuncs.com/imgtest/202301121548019.png)

   ![image-20230112154842650](https://icesoda-picgo.oss-cn-beijing.aliyuncs.com/imgtest/202301121548247.png)

- 改进：在配置中心该数据，all动态修改

  1. 在配置中心中新建对应服务的配置

     ![image-20230112155816631](https://icesoda-picgo.oss-cn-beijing.aliyuncs.com/imgtest/202301121558611.png)

     ![image-20230112155854948](https://icesoda-picgo.oss-cn-beijing.aliyuncs.com/imgtest/202301121558596.png)

  2. 在controller中添加注解   @RefreshScope   刷新配置

     ![image-20230112160010953](https://icesoda-picgo.oss-cn-beijing.aliyuncs.com/imgtest/202301121600906.png)

  3. 修改配置，无需重启动态更新

     ![image-20230112160142815](https://icesoda-picgo.oss-cn-beijing.aliyuncs.com/imgtest/202301121601616.png)

     ![image-20230112164239641](https://icesoda-picgo.oss-cn-beijing.aliyuncs.com/imgtest/202301121642317.png)

## 命名空间与配置分组

> ​	命名空间： 配置隔离
> 默认：public(保留空间)：默认新增的所有配置都在public空间
>
> 开发 测试 生产 : 利用命名空间来做环境隔离
> 注意：在bootstrap.properties: 配置上 需要使用哪个命名空间下的配置
> `spring.cloud.nacos.config.namespace=`
>
> ​	每一个微服务之间互相隔离配置，每一个微服务都创建自己的命名空间，只加载自己命名空间下的所有配置
>
> 配置集： 所有的配置的集合
>
> 配置集ID 类似配置文件名
> Data ID 类似配置文件名
>
> 配置分组
> 默认所有的配置集都属于：DEFAULT_GROUP：
> 1111, 618, 1212
>
> ​    每个微服务创建自己的命名空间。使用配置分组，区分环境，dev,test,prod
>
> ​    同时加载多个配置集
> ​    1 微服务任何配置信息 任何配置文件都可以放在配置中心中
> ​    2 只需要在bootstrap.properties说明加载配置中心中配置哪些配置文件即可
> ​    3 `@Value @ConfigurationProperties ...`
> ​    以前SpringBoot任何方式从配置文件中获取值 都能使用
> ​    配置中心有的优先使用配置中心中的

- 新建命名空间并添加对应配置

  ![image-20230112171835186](https://icesoda-picgo.oss-cn-beijing.aliyuncs.com/imgtest/202301121718183.png)

- 在bootstrap中添加配置信息 指定生效的命名空间

  ![image-20230112172858120](https://icesoda-picgo.oss-cn-beijing.aliyuncs.com/imgtest/202301121729165.png)

- 给每个微服务创建命名空间

  ![image-20230112173702480](https://icesoda-picgo.oss-cn-beijing.aliyuncs.com/imgtest/202301121737992.png)

  后续可以根据需求给各个微服务配置对应的命名空间

- 配置分组

  ![image-20230112174857458](https://icesoda-picgo.oss-cn-beijing.aliyuncs.com/imgtest/202301121748931.png)

  ![image-20230112174915712](https://icesoda-picgo.oss-cn-beijing.aliyuncs.com/imgtest/202301121749172.png)

  ![image-20230112175231900](https://icesoda-picgo.oss-cn-beijing.aliyuncs.com/imgtest/202301121752031.png)