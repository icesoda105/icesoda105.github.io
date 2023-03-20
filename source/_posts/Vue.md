---
title: Vue
categories:
  - [icesodaMall]
tags: [Vue,MVVM]
author: icesoda
toc: false
date: 2023-01-13 15:35:51
cover:
description:
---

## MVVM思想

- M: 模型，即Model，包括数据和一些基本操作
- V:  视图，即View，页面渲染结果
- VM: 即View-Model,模型与视图间的双向操作

## VUE

> Vue (读音 /vjuː/，类似于 view) 是一套用于构建用户界面的渐进式框架。与其它大型框架不同的是，Vue 被设计为可以自底向上逐层应用。Vue 的核心库只关注视图层，不仅易于上手，还便于与第三方库或既有项目整合。另一方面，当与现代化的工具链以及各种支持类库结合使用时，Vue 也完全能够为复杂的单页应用提供驱动。

- 安装

  通过 npm 安装。这种方式也是官网推荐的方式，需要 nodejs 环境。

  1、新建文件夹 hello-vue，并使用 vscode 打开

  2、使用 vscode 控制台，npm install -y；

  项目会生成 package-lock.json 文件，类似于 maven 项目的 pom.xml 文件。

  3、使用 npm install vue，给项目安装 vue；项目下会多 node_modules 目录，并且在下面有一个 vue 目录。

- **vue** **声明式渲染**

  页面代码

  ```javascript
  <body>
  
  <div id="app"><h1>{{name}}，非常帅！！！</h1>
  
  </div>
  
  <script src="./node_modules/vue/dist/vue.min.js"></script>
  
  <script>
  
  let vm = new Vue({
  
  el:"#app",
  
  data:{
  
  name: "张三"
  
  }
  
  });
  
  </script>
  
  </body>
  
   
  ```

  首先通过 new Vue()来创建 Vue 实例

  然后构造函数接收一个对象，对象中有一些属性：

  el：是 element 的缩写，通过 id 选中要渲染的页面元素，本例中是一个 div

  data：数据，数据是一个对象，里面有很多属性，都可以渲染到视图中

  name：这里我们指定了一个 name 属性

  页面中的`h2`元素中，我们通过{{name}}的方式，来渲染刚刚定义的 name 属性。

- **双向绑定**

  效果：我们修改表单项，num 会发生变化。我们修改 num，表单项也会发生变化。为了实时观察到这个变化，我们将 num 输出到页面。

  **我们不需要关注他们为什么会建立起来关联，以及页面如何变化，我们只需要做好数据和**

  **视图的关联即可（**MVVM）

- **事件处理**

  给页面添加一个按钮：

  ```javascript
  <body>
  
  <div id="app">
  
  <input type="text" v-model="num"><button v-on:click="num++">关注</button>
  
  <h2>
  
  {{name}}，非常帅！！！有{{num}}个人为他点赞。
  
  </h2>
  
  </div>
  
  <script src="./node_modules/vue/dist/vue.js"></script>
  
  <script>
  
  // 创建 vue 实例
  
  let app = new Vue({
  
  el: "#app", // el 即 element，该 vue 实例要渲染的页面元素
  
  data: { // 渲染页面需要的数据
  
  name: "张三",
  
  num: 5
  
  }
  
  });
  
  </script>
  
  </body>
  ```

  这里用`v-on`指令绑定点击事件，而不是普通的`onclick`，然后直接操作 num

  普通 click 是无法直接操作 num 的。

  未来我们会见到更多 v-xxx，这些都是 vue 定义的不同功能的指令。

  简单使用总结：

  1）、使用 Vue 实例管理 DOM

  2）、DOM 与数据/事件等进行相关绑定

  3）、我们只需要关注数据，事件等处理，无需关心视图如何进行修改