---
title: LeeCode 84. 柱状图中最大的矩形
author: icesoda
categories:
- [算法,单调栈]
date: 2022-08-08 16:29:19
description:
---

> 给定 n 个非负整数，用来表示柱状图中各个柱子的高度。每个柱子彼此相邻，且宽度为 1 。
>
> 求在该柱状图中，能够勾勒出来的矩形的最大面积。

```java
  public int largestRectangleArea(int[] heights) {

​    // 双指针 两头开工 超出时间限制

​    int sum = 0;

​    int len = heights.length;



​    for (int i = 0;i < len;i++) {

​      int right = i;

​      int left = i;



​      for (;left >= 0;left--) {

​        if (heights[left] < heights[i]) break;

​      }



​      for (;right <len;right++) {

​        if (heights[right] < heights[i]) break;

​      }



​      int w = right - left - 1;

​      int h = heights[i];

​      sum = Math.max(sum,w * h);

​    }

​    return sum;



​    // 动态规划

​    int len = heights.length;

​    int[] minLeftIndex = new int[len];

​    int[] maxRightIndex = new int[len];



​    // 记录左边第一个小于该柱子的下标

​    minLeftIndex[0] = -1;

​    // 要考虑左边 起始就为1

​    for (int i = 1;i < len;i++) {

​      int l = i - 1; // 左边

​      // 不断向右寻找

​      while (l >= 0 && heights[l] >= heights[i]) l = minLeftIndex[l];

​      minLeftIndex[i] = l;

​    }



​    // 记录右边第一个小于该柱子的下标

​    maxRightIndex[len - 1] = len;

​    for (int i = len - 2;i >= 0;i--) {

​      int r = i + 1;

​      // 不断向左寻找

​      while (r < len && heights[r] >= heights[i]) r = maxRightIndex[r];

​      maxRightIndex[i] = r;

​    }



​    // 求和

​    int result = 0;

​    for (int i = 0;i < len;i++) {

​      // 目标值即为对应基准上所对应的面积大小 5——10,6——6

​      // 找到俩小 中间部分一定为大 可覆盖区域

​      int sum = heights[i] * (maxRightIndex[i] - minLeftIndex[i] - 1);

​      result = Math.max(sum,result);

​    }

​    return result;



​    // 单调栈 头底 从大到小

​    Stack<Integer> st = new Stack<Integer>();

​    int len = heights.length;

​    // 数组扩容 在头和尾各加入一个元素

​    int[] newHeights = new int[len + 2];

​    // 左右测试 始末初始化

​    

​    newHeights[0] = 0;

​    newHeights[newHeights.length - 1] = 0;



​    // 重新遍历分配

​    for (int i = 0; i < len; i++) {

​      newHeights[i + 1] = heights[i];

​    }

​    // 扩容后的数组还给原数组

​    heights = newHeights;

​    len = newHeights.length;



​    st.push(0);

​    int result = 0;



​    for (int i = 1;i < len;i++) {

​      // 当前大于前一个柱子入栈

​      if (heights[i] > heights[st.peek()]) {

​        st.push(i);



​      } else if (heights[i] == heights[st.peek()]) {

​        st.pop();

​        st.push(i);

​      } else {

​        while (!st.isEmpty() && heights[i] < heights[st.peek()]) {

​          int mid = st.peek();

​          st.pop();

​          int left = st.peek();

​          int right = i;

​          int w = right - left - 1;

​          int h = heights[mid];

​          result = Math.max(result,w * h);

​        }

​        st.push(i);

​      }

​    }

​    return result;

  }
```

