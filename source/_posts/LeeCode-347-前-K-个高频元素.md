---
title: LeeCode 347.前 K 个高频元素
categories:
- [算法,栈和队列]
author: icesoda
date: 2022-08-27 09:43:04
description:
---

> 给定一个非空的整数数组，返回其中出现频率前 k 高的元素
>
> // 对频率进行排序 使用容器适配器 优先级队列
>
> ​    // 优先级队列 就是一个披着队列外衣的堆 对外接口只是从队头取元素，从队尾添加元素
>
> ​    // 优先级队列内部元素是自动按照元素的权值排列
>
> ​    // 缺省情况下priority_queue利用max-heap（大顶堆）完成对元素的排序
>
> ​    // 这个大顶堆是以vector为表现形式的complete binary tree（完全二叉树）
>
> 
>
> ​    // 堆是一颗完全二叉树 树中的每个节点的值都不小于或不大于其左右孩子的值
>
> ​    // 如果父节点是大于等于左右孩子的就是大顶堆 反之小顶堆
>
> ​    // 用小顶堆 每次将最小的元素弹出 最后积累的就是前K个最大元素

```java
    public int[] topKFrequent(int[] nums, int k) {
        // 存结果
        int[] result = new int[k];
        // 定义一个哈希表存值频率
        HashMap<Integer,Integer> map = new HashMap<>();
        // 1. 统计每个数的频率
        for (int num : nums) {
            // hash.put(c,hash.getOrDefault(c,0)+1); //若没有就是0，若有就是原有值增一。
            map.put(num,map.getOrDefault(num,0) + 1);
        }

        // map有一个方法叫做entrySet,这方法可以将Map的键值对的映射关系作为set集合的元素存储到Set集合当中，
        // 而这种映射关系的类型就是Entry的类型。
        // 因此可以通过使用Getkey()和getvalue()两个方法得到Set中存储的键和值。

        Set<Map.Entry<Integer,Integer>> entries = map.entrySet();
        // 2. 根据map的value值 构建一个大顶堆
        PriorityQueue<Map.Entry<Integer,Integer>> queue = new PriorityQueue<>((o1,o2) -> (o2.getValue() - o1.getValue())); 
        // 3. 遍历记录好数值频率的哈希表 放进大顶堆
        for (Map.Entry<Integer,Integer> entry : entries) {
            queue.offer(entry);
        }

        // 以k为界限 获取k个最高频率的值
        for (int i = k - 1;i >= 0;i--) {
            result[i] = queue.poll().getKey();
        }
        return result;
    }
```

