---
title: LeeCode. 1047. 删除字符串中的所有相邻重复项
author: icesoda
date: 2022-08-15 10:33:25
categories:
- [算法,栈和队列]
description:
---
> 给出由小写字母组成的字符串 S，重复项删除操作会选择两个相邻且相同的字母，并删除它们。
>
> 在 S 上反复执行重复项删除操作，直到无法继续删除。
>
> 在完成所有重复项删除操作后返回最终的字符串。答案保证唯一。
>

```java
    public String removeDuplicates(String s) {
        // 继续消消乐
        // 使用Deque作为堆栈
        // ArrayDeque会比LinkedList在除了删除元素这一点外会快一点
        ArrayDeque<Character> deque = new ArrayDeque<>();
        char ch;

        for (int i = 0;i < s.length();i++) {
            ch = s.charAt(i);

            // 空队列 或 不匹配时入栈
            if (deque.isEmpty() || deque.peek() != ch) {
                deque.push(ch);
            } else {
                // 匹配时消除
                deque.pop();
            }
        }

        String str = "";
        // 收集剩余元素
        while (!deque.isEmpty()) {
            str = deque.pop() + str;
        }
        return str;

        // 用字符串直接作为栈 省去栈转为字符串的操作
        // 将res当做栈
        StringBuffer res = new StringBuffer();
        // res的长度
        int top = -1;

        for (int i = 0;i < s.length();i++) {
            char c = s.charAt(i);
            // 当top >0 即栈中有字符时，当前字符如果和栈中字符相等，弹出栈顶字符
            if (top >= 0 && res.charAt(top) == c) {
                res.deleteCharAt(top);
                top--;
            } else {
                // 否则 将该字符入栈
                res.append(c);
                top++;
            }
        }
        return res.toString();
    }

    // 双指针
    char[] ch = s.toCharArray();
    int fast = 0;
    int slow = 0;

    while (fast < s.length()) {
        // 直接用fast指针覆盖slow指针的值
        ch[slow] = ch[fast]; 
        // 遇到前后相同值得 就跳过 slow后退一步 下次循环就可以直接覆盖掉
        if (slow > 0 && ch[slow] == ch[slow - 1]) {
            slow--;
        } else {
            slow++;
        }
        fast++;
    }
    // 返回一个新的字符串
    return new String(ch,0,slow);
}
```

