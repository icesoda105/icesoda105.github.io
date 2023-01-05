---
title: LeeCode 239. 滑动窗口最大值
categories:
- [算法,栈和队列]
author: icesoda
date: 2022-08-27 09:32:02
description:
---
> 给你一个整数数组 nums，有一个大小为 k 的滑动窗口从数组的最左侧移动到数组的最右侧。你只可以看到在滑动窗口内的 k 个数字。滑动窗口每次只向右移动一位。
>
> 返回 滑动窗口中的最大值 。
>

```java
public int[] maxSlidingWindow(int[] nums, int k) {
        // 队列一进一出维护窗口内元素 单调队列（单调递减） 
        // 由大到小(队列元素排队，将最大值放在出口)

        // 定义一个单调队列
        ArrayDeque<Integer> deque = new ArrayDeque<>();
        int n = nums.length;
        // 存取最大值 个数为：n-k+1
        int[] res = new int[n - k + 1];
        int index = 0;

        for (int i = 0;i < n; i++) {
            // i为nums下标 要在[i - k + 1,i]中选到最大值，只需要保证两点
            // 1. 队列头结点需要在此范围内（每个滑动窗口内） 不符合弹出
            while(!deque.isEmpty() && deque.peek() < i - k + 1) {
                deque.poll();
            }

            // 2. 既然是单调 就要保证每次放进去的数字要比末尾的都大  否则弹出
            while (!deque.isEmpty() && nums[deque.peekLast()] < nums[i]) {
                deque.pollLast();
            }

            // 筛选后入队列
            deque.offer(i);

            // 当i增长到满足第一个滑动窗口范围的时候，每滑动一步就将队列头结点记录在res里
            if (i >= k - 1) {
                res[index++] = nums[deque.peek()];
            }
        }
        return res;
    }
```

