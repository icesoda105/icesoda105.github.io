---
title: 配置&测试微服务基本CRUD功能
author: icesoda
date: 2022-12-12 09:36:06
categories:
- [icesodaMall]
description:
---

### 整合Mybatis-Plus

- 导入依赖

- 配置

  1. 配置数据库

     - 导入数据库驱动(对应数据库版本)

  2. 配置MyBatis-Plus

     - 使用MapperScan
     - 告诉Mybatis-Plus，sql映射文件位置

     ![image-20221212095723955](https://cdn.jsdelivr.net/gh/icesoda105/PicgoWorkspace/img/image-20221212095723955.png)

     

- 测试向数据库添加数据

  ![image-20221212105303171](https://cdn.jsdelivr.net/gh/icesoda105/PicgoWorkspace/img/image-20221212105303171.png)

  ![image-20221212105328165](https://cdn.jsdelivr.net/gh/icesoda105/PicgoWorkspace/img/image-20221212105328165.png)

- 修改数据

  ![image-20221212110047746](https://cdn.jsdelivr.net/gh/icesoda105/PicgoWorkspace/img/image-20221212110047746.png)

  ![image-20221212110118622](https://cdn.jsdelivr.net/gh/icesoda105/PicgoWorkspace/img/image-20221212110118622.png)

- 查询数据

  ![image-20221212110718033](https://cdn.jsdelivr.net/gh/icesoda105/PicgoWorkspace/img/image-20221212110718033.png)