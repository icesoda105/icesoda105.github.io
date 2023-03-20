---
title: LeeCode 503. 下一个更大元素 II
categories:
- [算法,单调栈]
author: icesoda
date: 2022-08-05 11:40:15
description:
---
> 给定一个循环数组 nums （ nums[nums.length - 1] 的下一个元素是 nums[0] ），返回 nums 中每个元素的 下一个更大元素 。
>
> 数字 x 的 下一个更大的元素 是按数组遍历顺序，这个数字之后的第一个比它更大的数，这意味着你应该循环地搜索它的下一个更大的数。如果不存在，则输出 -1 。
>

**单调栈   实现循环数组 二倍数组长度**

```java
public int[] nextGreaterElements(int[] nums) {
        // 循环数组 
        int n = nums.length;
        int[] result = new int[n];
        // 初始化
        Arrays.fill(result,-1);

        // 开始单调栈
        Stack<Integer> st = new Stack<>();
        // 下标入栈
        st.add(0);
        for (int i = 0;i < n * 2 - 1;i++) {

            while (!st.isEmpty() && nums[i % n] > nums[st.peek()]) {
                result[st.peek()] = nums[i % n];
                st.pop();
            }
            st.push(i % n);
        }
        return result;
    }
```

