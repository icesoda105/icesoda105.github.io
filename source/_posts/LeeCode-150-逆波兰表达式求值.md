---
title: LeeCode 150. 逆波兰表达式求值
categories:
- [算法,栈和队列]
author: icesoda
date: 2022-08-22 11:12:00
description:
---
> 根据 逆波兰表示法，求表达式的值。
>
> 有效的算符包括 +、-、*、/ 。每个运算对象可以是整数，也可以是另一个逆波兰表达式。
>
> 注意 两个整数之间的除法只保留整数部分。
>
> 可以保证给定的逆波兰表达式总是有效的。换句话说，表达式总会得出有效数值且不存在除数为 0 的情况。
>

```Java
public int evalRPN(String[] tokens) {
    // 逆波兰表达式相当于是二叉树中的后序遍历
    Deque<Integer> stack = new LinkedList();

    for (String s : tokens) {
        // 判断字符串是否相等 
        if ("+".equals(s)) {
            // 遇到加号，两数出栈做加法
            stack.push(stack.pop() + stack.pop());

        } else if ("-".equals(s)) {
            // 遇到减号，两数出栈做减法(因为先进后出需要逆序)
            stack.push( - stack.pop() + stack.pop());

        } else if ("*".equals(s)) {
            // 遇到乘号，两数出栈做乘法
            stack.push(stack.pop() * stack.pop());

        } else if ("/".equals(s)) {
            // 遇到除号，两数出栈做除法(先进后出逆序安排)
            int temp1 = stack.pop();
            int temp2 = stack.pop();
            stack.push(temp2 / temp1);
        } else {
            // 类型转换：字符串->int
            stack.push(Integer.valueOf(s));
        }
    }
    return stack.pop();
}
```

