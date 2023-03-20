---
title: Java基础知识
author: icesoda
date: 2022-08-28 14:13:06
categories:
- [Java基础]
description:
---

![740942_1470042423855_86F5A9F9F791DD7EA7C96F158F0FEA87](https://cdn.jsdelivr.net/gh/icesoda105/PicgoWorkspace/img/740942_1470042423855_86F5A9F9F791DD7EA7C96F158F0FEA87.jpg)

#### 定义

- 双向队列的定义

  `Deque<Character> deque = new LinkedList<>();`

  `ArrayDeque<Character> deque = new ArrayDeque<>();`
  
- 单调队列的定义

  `ArrayDeque<Integer> deque = new ArrayDeque<>();`

- 栈的定义

  `Deque<Integer> stack = new LinkedList<>();`

- 哈希表的定义

  `HashMap<Integer,Integer> map = new HashMap<>();`

- entrySet的定义

  `Set<Map.Entry<Integer,Integer>> entrise = map.entrySet();`

- 优先级队列定义大顶堆

  `PriorityQueue<Map.Entry<Integer,Integer>> queue= new PriorityQueue<>((o1,o2) -> (o2.getValue() - o1.getValue()));`

#### 方法及属性

1. **ArrayList**	`import java.util.ArrayList;`

   ​	`ArrayList<E> objectName = new ArrayList<>();`  

   - get();	访问元素
   - set();     修改元素
   - remove();    删除元素

   **适用**：

   			1. 频繁访问列表中的某一个元素。

      			2. 只需要在列表末尾进行添加和删除元素操作。

2. LinkedList     `import java.util.LinkedList;`

   **适用**：

      1. 需要通过循环迭代来访问列表中的某些元素。
      2. 需要频繁的在列表开头、中间、末尾等位置进行添加和删除元素操作。

#### 将字符串转为字符数组

- `char[] ch = s.toCharArray();`

#### 返回一个新的字符串

- `return new String(ch,0,end);`