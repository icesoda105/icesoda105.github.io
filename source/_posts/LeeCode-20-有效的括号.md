---
title: LeeCode. 20. 有效的括号
author: icesoda
date: 2022-08-15 10:15:05
categories:
- [算法,栈和队列]
description:
---
> 给定一个只包括 '('，')'，'{'，'}'，'['，']' 的字符串 s ，判断字符串是否有效。
>
> 有效字符串需满足：
>
> 左括号必须用相同类型的右括号闭合。
> 左括号必须以正确的顺序闭合。

```java
class Solution {
    public boolean isValid(String s) {
        // 定义一个字符型双向队列
        Deque<Character> deque = new LinkedList<>();
        char ch;

        // 定义匹配入栈规则及遍历出栈消消乐
        for (int i = 0;i < s.length();i++) {
            // 将字符串转换为字符
            ch = s.charAt(i);

            if (ch == '(') {
                deque.push(')');
            } else if (ch == '[') {
                deque.push(']');
            } else if (ch == '{') {
            deque.push('}');
            
            // 如果队列里有字符 且字符不匹配
            } else if (deque.isEmpty() || deque.peek() != ch) {
                return false;
            // 如果是右括号判断是否和栈顶元素匹配 相同则消除
            } else {
                deque.pop();
            }
        }
        return deque.isEmpty();
    }
}
```

