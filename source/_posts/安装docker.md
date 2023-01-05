---
title: 安装docker
author: icesoda
date: 2022-11-11 15:43:31
categories:
description:
---

### docker
#### ：虚拟化容器技术，docker基于镜像，可以秒级启动各种容器。每一种容器都是一个完整的运行环境，容器之间互相隔离。

- 卸载之前的docker

  ![image-20221111160409130](D:/Program Files/Typora/resources/image/image-20221111160409130.png)

- 安装依赖

  ![image-20221111160643690](D:/Program Files/Typora/resources/image/image-20221111160643690.png)

  ![image-20221111160703937](D:/Program Files/Typora/resources/image/image-20221111160703937.png)

- 安装地址

  ![image-20221111160828423](D:/Program Files/Typora/resources/image/image-20221111160828423.png)

- 安装docker以及 docker-cli docker的引擎、操作docker的客户端和它的容器

  ![image-20221111161337161](D:/Program Files/Typora/resources/image/image-20221111161337161.png)

  ![image-20221111161356534](D:/Program Files/Typora/resources/image/image-20221111161356534.png)

- 启动docker及设置开机自启

  ![image-20221111161630998](D:/Program Files/Typora/resources/image/image-20221111161630998.png)

  ![image-20221111161739522](D:/Program Files/Typora/resources/image/image-20221111161739522.png)

- 配置docker国内的镜像加速（阿里云）方便后续安装mysql、redis

  ![image-20221111162218713](D:/Program Files/Typora/resources/image/image-20221111162218713.png)

  ![image-20221111162309209](D:/Program Files/Typora/resources/image/image-20221111162309209.png)

  ![image-20221111162442526](D:/Program Files/Typora/resources/image/image-20221111162442526.png)

- docker安装mysql

  ![image-20221111162756000](D:/Program Files/Typora/resources/image/image-20221111162756000.png)

  ![image-20221111163717724](D:/Program Files/Typora/resources/image/image-20221111163717724.png)

- 创建实例并启动

  ```
  docker run -p 3306:3306 --name mysql \
  
  -v /mydata/mysql/log:/var/log/mysql \
  
  -v /mydata/mysql/data:/var/lib/mysql \
  
  -v /mydata/mysql/conf:/etc/mysql \
  
  -e MYSQL_ROOT_PASSWORD=root \
  
  -d mysql:5.7
  ```

  参数说明

  > -p 3306:3306：将容器的 3306 端口映射到主机的 3306 端口
  >
  > -v /mydata/mysql/conf:/etc/mysql：将配置文件夹挂载到主机
  >
  > -v /mydata/mysql/log:/var/log/mysql：将日志文件夹挂载到主机
  >
  > -v /mydata/mysql/data:/var/lib/mysql/：将配置文件夹挂载到主机
  >
  > -e MYSQL_ROOT_PASSWORD=root：初始化 root 

- 切换root用户

  账号密码： vagrant

  ![image-20221111164331983](D:/Program Files/Typora/resources/image/image-20221111164331983.png)

- 主机测试虚拟机安装的mysql

- ![image-20221111164644679](D:/Program Files/Typora/resources/image/image-20221111164644679.png)

  ![image-20221111164737720](D:/Program Files/Typora/resources/image/image-20221111164737720.png)

  - mysql 一个完整且独立的运行环境 处于一个微型的Linux环境中

  ![image-20221111165409920](D:/Program Files/Typora/resources/image/image-20221111165409920.png)

  - mysql配置文件的修改

  ![image-20221111174724965](D:/Program Files/Typora/resources/image/image-20221111174724965.png)

- docker安装redis

  - 下载镜像

    ![image-20221114125704629](D:/Program Files/Typora/resources/image/image-20221114125704629.png)

  - 创建实例并启动

    ![image-20221114130214450](D:/Program Files/Typora/resources/image/image-20221114130214450.png)

    ![image-20221114130452568](D:/Program Files/Typora/resources/image/image-20221114130452568.png)

  - 默认持久化

    ![image-20221114130935287](D:/Program Files/Typora/resources/image/image-20221114130935287.png)

    ![image-20221114131001613](D:/Program Files/Typora/resources/image/image-20221114131001613.png)

    ![image-20221114131349501](D:/Program Files/Typora/resources/image/image-20221114131349501.png)

  - redis可视化客户端

    ![image-20221114131442405](D:/Program Files/Typora/resources/image/image-20221114131442405.png)

    ![image-20221114131650131](D:/Program Files/Typora/resources/image/image-20221114131650131.png)

    ![image-20221114131721883](D:/Program Files/Typora/resources/image/image-20221114131721883.png)

    ![image-20221114132103861](D:/Program Files/Typora/resources/image/image-20221114132103861.png)

  - redis官方文档

    ![image-20221114132423894](D:/Program Files/Typora/resources/image/image-20221114132423894.png)

    ![image-20221114132540825](D:/Program Files/Typora/resources/image/image-20221114132540825.png)