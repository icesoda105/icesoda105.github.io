---
title: LeeCode 42. 接雨水
categories:
- [算法,单调栈]
author: icesoda
date: 2022-08-08 10:08:54
description:
---

> 给定 n 个非负整数表示每个宽度为 1 的柱子的高度图，计算按此排列的柱子，下雨之后能接多少雨水。

```java
public int trap(int[] height) {

   // 双指针

​    int sum = 0;

​    // 第一个指针指向当前柱子

​    for (int i = 0;i < height.length;i++) {

​      // 首尾柱子不接雨水 免测

​      if (i == 0 || i == height.length - 1) continue;



​      // 初始都为所在柱子高度 动态变化的

​      int rHeight = height[i]; // 记录右边柱子的最高高度

​      int lHeight = height[i]; // 记录左边柱子的最高高度



​      // 第二个指针指向前后柱子

​      // 遍历更新右柱子最高高度

​      for (int r = i + 1;r < height.length;r++) {

​        if (height[r] > rHeight) rHeight = height[r]; 

​      }



​      // 遍历更新左柱子最高高度

​      for (int l = i - 1;l >= 0;l--) {

​        if (height[l] > lHeight) lHeight = height[l];

​      }



​      // 左右柱子取最小与当前柱子相减

​      int h = Math.min(lHeight,rHeight) - height[i];



​      // 动态累加

​      if (h > 0) sum += h;

​    }

​    return sum;



​    // 动态规划

​    // 当前列雨水面积：min(左边柱子的最高高度，记录右边柱子的最高高度) - 当前柱子高度。

​    int len = height.length;

​    if (len <= 2) return 0;

​    int[] maxLeft = new int[len];

​    int[] maxRight = new int[len];



​    // 记录每个柱子左边柱子最大高度

​    maxLeft[0] = height[0];

​    for (int i = 1;i < len;i++) 

​      maxLeft[i] = Math.max(height[i],maxLeft[i-1]);



​    // 记录每个柱子右边柱子最大高度

​    maxRight[len - 1] = height[len - 1];

​    for (int i = len - 2;i >= 0;i--) 

​      maxRight[i] = Math.max(height[i],maxRight[i+1]);



​    // 求和

​    int sum = 0;

​    for (int i = 0;i < len;i++) {

​      int count = Math.min(maxLeft[i],maxRight[i]) - height[i];

​      if (count > 0) sum += count;

​    }

​    return sum;



​    // 单调栈 头底从小到大

​    // 栈头元素就是凹槽底部的柱子，栈头第二个元素就是凹槽左边的柱子，而添加的元素就是凹槽右边的柱子

​    int len = height.length;

​    if (len <= 2) return 0;



​    Stack<Integer> stack = new Stack<Integer>();

​    // 下标入栈

​    stack.push(0);



​    int sum = 0;

​    // 右边柱子入栈判断

​    for (int i = 1;i < len;i++) {

​       // 右边柱子小则入栈

​      if (height[i] < height[stack.peek()]) {

​        stack.push(i);



​      // 高度相等 则弹出后者替换,高度差在即可

​      } else if (height[i] == height[stack.peek()]) {

​        stack.pop();

​        stack.push(i);

​      

​      // 大于栈顶高度

​      } else {

​        while (!stack.isEmpty() && (height[i] > height[stack.peek()])) {

​          // 则中间值即为弹出的凹槽柱子

​          int mid = stack.pop();



​          if (!stack.isEmpty()) {

​            // 下一栈顶即为左柱子

​            int left = stack.peek();



​            int h = Math.min(height[left],height[i]) - height[mid];

​            int w = i - left - 1;

​            int s = h * w;

​            if (s > 0) sum += s;

​          }

​        }

​        stack.push(i);

​      }

​    }

​    return sum;

  }
```

