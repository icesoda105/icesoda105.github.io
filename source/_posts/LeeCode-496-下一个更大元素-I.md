---
title: LeeCode-496. 下一个更大元素 I
categories:
- [算法,单调栈]
author: icesoda
date: 2022-08-04 18:26:35
description:
---
> nums1 中数字 x 的 下一个更大元素 是指 x 在 nums2 中对应位置 右侧 的 第一个 比 x 大的元素。
>
> 给你两个 没有重复元素 的数组 nums1 和 nums2 ，下标从 0 开始计数，其中nums1 是 nums2 的子集。
>
> 对于每个 0 <= i < nums1.length ，找出满足 nums1[i] == nums2[j] 的下标 j ，并且在 nums2 确定 nums2[j] 的 下一个更大元素 。如果不存在下一个更大元素，那么本次查询的答案是 -1 。
>
> 返回一个长度为 nums1.length 的数组 ans 作为答案，满足 ans[i] 是如上所述的 下一个更大元素 。
>

**单调栈  哈希表去重**

```java
public int[] nextGreaterElement(int[] nums1, int[] nums2) {
        // 单调栈 从头到底 单调递增
        Stack<Integer> temp = new Stack<>();
        // 需要定义一个和nums1一样大小的数组result来存放结果
        int[] res = new int[nums1.length];
        // 初始化为-1
        Arrays.fill(res,-1);
        // 关键： 两个没有重复元素的数组 用map做映射
        HashMap<Integer,Integer> hashMap = new HashMap<>();

        // 把数组1的信息(下标元素，下标)录入哈希表 
        for (int i = 0;i < nums1.length;i++) {
            hashMap.put(nums1[i],i);
        } 
        // 栈初始下标入栈
        temp.add(0);

        // 遍历数组2
        for (int i = 0;i < nums2.length;i++) {
            // 小于等于栈顶下标对应的值 入栈
            if (nums2[i] <= nums2[temp.peek()]) {
                temp.add(i);
            } else {
                // 大于栈顶下标对应的值
                while (!temp.isEmpty() && nums2[temp.peek()] < nums2[i]) {
                    // 判断nums1中是否有这个测试值
                    if (hashMap.containsKey(nums2[temp.peek()])) {
                        // 获取测试值所在下标
                        Integer index = hashMap.get(nums2[temp.peek()]);
                        // 在结果数组中同步下标，记录对应目标值
                        res[index] = nums2[i];
                    }
                    // 弹出
                    temp.pop();
                }
                // 下一个
                temp.add(i);
            }
        }
        return res;
    }
```

