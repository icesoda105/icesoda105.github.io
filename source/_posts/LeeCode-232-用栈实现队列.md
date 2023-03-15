---
title: LeeCode. 232. 用栈实现队列
author: icesoda
date: 2022-08-14 09:58:39
categories:
- [算法,栈和队列]
description:
---
> 请你仅使用两个栈实现先入先出队列。队列应当支持一般队列支持的所有操作（push、pop、peek、empty）：
>
> 实现 MyQueue 类：
>
> void push(int x) 将元素 x 推到队列的末尾
> int pop() 从队列的开头移除并返回元素
> int peek() 返回队列开头的元素
> boolean empty() 如果队列为空，返回 true ；否则，返回 false
> 说明：
>
> 你 只能 使用标准的栈操作 —— 也就是只有 push to top, peek/pop from top, size, 和 is empty 操作是合法的。
> 你所使用的语言也许不支持栈。你可以使用 list 或者 deque（双端队列）来模拟一个栈，只要是标准的栈操作即可。

```java
class MyQueue {
    // 使用栈来模拟队列的行为，如果仅仅用一个栈，是一定不行的，所以需要两个栈一个输入栈，一个输出栈
    Stack<Integer> stackIn;
    Stack<Integer> stackOut;

    public MyQueue() {
        stackIn = new Stack<>(); // 负责进栈
        stackOut = new Stack<>(); // 负责出栈
    }
    
    public void push(int x) {
        stackIn.push(x);
    }
    
    public int pop() {
        dumpstackIn(); // 调用辅助函数
        int out = stackOut.pop();
        return out;
    }
    
    public int peek() {
        dumpstackIn(); // 调用辅助函数
        int out = stackOut.peek();
        return out;
    }
    
    public boolean empty() {
        boolean i = stackIn.isEmpty() && stackOut.isEmpty();
        return i;
    }

    // 辅助函数
    // 如果出栈里为空 那么将入栈中的元素全部放出栈中
    private void dumpstackIn() {
        if (!stackOut.isEmpty()) return;

        while (!stackIn.isEmpty()) {
            stackOut.push(stackIn.pop());
        }
    }
}
```

