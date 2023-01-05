---
title: 分布式组件-SpringCloud-Alibaba
author: icesoda
date: 2022-12-12 14:49:53
categories:
- [icesodaMall]
description:
---

### 微服务-注册中心-配置中心-网关

![image-20221212145658041](D:/Program Files/Typora/resources/image/image-20221212145658041.png)

- 注册中心：Service Discovery :

  ​		Spring Cloud Netflix : Eureka

- 配置中心：Spring Cloud Config :

  ​		Spring Cloud Netflix : Zuul

- 本项目使用的是SpringCloud Alibaba提供的分布式组件
  - 微服务开发的一站式解决方案，包含开发分布式应用微服务的必需组件
  - 只需要添加一些注解和少量配置，就可以将SpringCloud Alibaba应用接入阿里微服务解决方案，通过阿里中间件来迅速搭建分布式应用系统。

- SpringCloud:
  - 部分组件停止维护和更新，给开发带来不便。
  - 部分环境搭建复杂，没有完善的可视化界面，需要大量的二次开发和定制。
  - 配置复杂，难以上手，部分配置差别难以区分和合理应用。

- SpringCloud Alibaba的优势：

  阿里使用过的组件经历了考验，性能强悍，设计合理，现在开源出来大家用成套的产品搭配完善的可视化界面给开发运维带来极大的便利。搭建简单，学习曲线低。

- 结合SpringCloud Alibaba 最终的技术搭配方案：

  - SpringCloud Alibaba - Nacos: 注册中心（服务发现、注册）
  - SpringCloud Alibaba - Nacos: 配置中心（动态配置管理）
  - SpringCloud - Ribbon: 负载均衡
  - SpringCloud - Feign: 声明式HTTP客户端（调用远程服务）
  - SpringCloud Alibaba - Sentinel: 服务容错（限流、降级、熔断）
  - SpringCloud - Gateway: API网关（webflux编程模式）
  - SpringCloud - Sleuth: 调用链监控
  - SpringCloud Alibaba - Seata: 原 Fescar，即分布式事务解决方案

- 组件

  - Sentinel: 把流量作为切入点，从流量控制、熔断降级、系统负载保护等多个维护保护服务的稳定性。
  - Nacos: 一个更易于构建云原生应用的动态服务发现、配置管理和服务管理平台。
  - RocketMQ:一款开源的分布式消息系统，基于高可用分布式集群技术，提供低延时的、高可靠的消息发布与订购服务。
  - Dubbo: Apache Dubbo(TM)是一款高性能Java RPC框架。
  - Seata：阿里巴巴开源产品，一个易于使用的高性能微服务分布式事务解决方案。
  - Alibaba Cloud ACM: 一款在分布式架构环境中对应用配置进行集中管理和推送的应用配置中心产品。
  - Alibaba Cloud OSS: 阿里云对象存储服务（Object Storage Service,简称 OSS），是阿里云提供的海量、安全、低成本、高可靠的云存储服务。可以在任何应用、任何时间、任何地点存储和访问任意类型的数据。