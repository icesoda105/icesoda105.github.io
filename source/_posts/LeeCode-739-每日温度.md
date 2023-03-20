---
title: LeeCode 739.每日温度
categories:
- [算法,单调栈]
author: icesoda
date: 2022-08-03 16:41:49
description:
---
> 给定一个整数数组 temperatures ，表示每天的温度，返回一个数组 answer ，其中 answer[i] 是指对于第 i 天，下一个更高温度出现在几天后。如果气温在这之后都不会升高，请在该位置用 0 来代替。
>

​	**单调栈**

```java
public int[] dailyTemperatures(int[] temperatures) {
        // 从栈头到栈底递增
        int lens = temperatures.length;
        int []res = new int[lens];

        Deque<Integer> stack = new LinkedList<>();
        // 将温度数组第一个元素下标入栈
        stack.push(0);

        // 遍历温度数组逐个判断入栈
        for (int i = 1;i < lens;i++) {
            if (temperatures[i] <= temperatures[stack.peek()]) {
                // 小于的话直接压入栈中
                stack.push(i);
            } else {
                // 积攒栈元素循环记录 栈顶一直在更新
                while (!stack.isEmpty() && temperatures[i] > temperatures[stack.peek()]) {
                    // 遇到第一个大于的 取差值
                    res[stack.peek()] = i - stack.peek();
                    // 记录过的弹出
                    stack.pop();
                }
                // 下一个值的下标入栈
                stack.push(i);
            }
        }
        return res;
    }
```

