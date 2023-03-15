---
title: Gateway创建&测试API网关
categories:
  - [icesodaMall]
tags: [Gateway,SpingCloud]
author: icesoda
toc: false
date: 2023-01-13 10:23:30
cover:
description:
---

- 创建网关 依赖common   并修改各依赖版本

  ![image-20230113102617630](https://icesoda-picgo.oss-cn-beijing.aliyuncs.com/imgtest/202301131026248.png)

- 开启服务的注册发现

  ![image-20230113102930535](https://icesoda-picgo.oss-cn-beijing.aliyuncs.com/imgtest/202301131029757.png)

- 配置nacos的注册中心地址

  ![image-20230113103025197](https://icesoda-picgo.oss-cn-beijing.aliyuncs.com/imgtest/202301131030284.png)

- 命名空间

  ![image-20230113103228750](https://icesoda-picgo.oss-cn-beijing.aliyuncs.com/imgtest/202301131032785.png)

  ![image-20230113103450503](https://icesoda-picgo.oss-cn-beijing.aliyuncs.com/imgtest/202301131034415.png)

- 排除和数据源有关的配置

  ![image-20230113103734234](https://icesoda-picgo.oss-cn-beijing.aliyuncs.com/imgtest/202301131037766.png)

  `@SpringBootApplication(exclude = {DataSourceAutoConfiguration.class})`

  网关还没有用到数据库，但是common里有这个依赖，所以要排除

- 配置网关所使用的的端口

  `server.port=88`

  ![image-20230113103930547](https://icesoda-picgo.oss-cn-beijing.aliyuncs.com/imgtest/202301131039710.png)

- 配置网关路由规则

  ![image-20230113104313900](https://icesoda-picgo.oss-cn-beijing.aliyuncs.com/imgtest/202301131043086.png)

  `http://localhost:88/hello?url=weibo`

  ![image-20230113105133649](https://icesoda-picgo.oss-cn-beijing.aliyuncs.com/imgtest/202301131051563.png)