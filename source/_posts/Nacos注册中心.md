---
title: Nacos注册中心
author: icesoda
date: 2022-12-12 16:41:19
categories:
- [icesodaMall]
description:
---

- 将Nacos作为注册中心

1. 给common中添加服务注册功能，Nacos依赖

   ![image-20221212165628780](D:/Program Files/Typora/resources/image/image-20221212165628780.png)

2. 在应用的/src/main/res/application.properties配置文件中配置Nacos Server地址

   - 首先安装启动Nacos

     ![image-20221212172718855](D:/Program Files/Typora/resources/image/image-20221212172718855.png)

     ![image-20221212172750277](D:/Program Files/Typora/resources/image/image-20221212172750277.png)

     ![image-20221212174531134](D:/Program Files/Typora/resources/image/image-20221212174531134.png)
     
   - 使用@EnableDiscoveryClient注解开启服务注册与发现功能
   
     ![image-20221213092900229](D:/Program Files/Typora/resources/image/image-20221213092900229.png)
   
   - 登录nacos（账号密码默认：nacos）
   
     ![image-20221213093059994](D:/Program Files/Typora/resources/image/image-20221213093059994.png)
   
     ![image-20221213093151363](D:/Program Files/Typora/resources/image/image-20221213093151363.png)
   
   - 此时是没有应用注册到
   
     ![image-20221213093327634](D:/Program Files/Typora/resources/image/image-20221213093327634.png)
   
   - 在yml中添加服务名
   
     ![image-20221213093847698](D:/Program Files/Typora/resources/image/image-20221213093847698.png)
   
   - 重启
   
     ![image-20221213094029037](D:/Program Files/Typora/resources/image/image-20221213094029037.png)

- 将Nacos作为配置中心

  ![image-20221213100350157](D:/Program Files/Typora/resources/image/image-20221213100350157.png)

