---
title: LeeCode. 225. 用队列实现栈
author: icesoda
date: 2022-08-15 09:47:44
categories:
- [算法,栈和队列]
description:
---

```java
class MyStack {
    // 两个队列模拟一个栈
    Queue<Integer> que1;
    Queue<Integer> que2; // 辅助队列 用来备份

    public MyStack() {
        que1 = new LinkedList<>();
        que2 = new LinkedList<>();

    }
    
    public void push(int x) {
        que2.offer(x); // 先放在辅助队列中
        while (!que1.isEmpty()) {
            que2.offer(que1.poll());
        }

        // 交换 放进que1中
        Queue<Integer> queueTemp;
        queueTemp = que1;
        que1 = que2;
        que2 = queueTemp;
    }
    
    public int pop() {
        return que1.poll();
    }
    
    public int top() {
        return que1.peek();
    }
    
    public boolean empty() {
        return que1.isEmpty();
    }

    // 使用两个Deque实现一个栈
    // Deque接口继承了Queue接口
    // 所以Queue中的add、poll、peek等效于Deque中的addLast、pollFirst、peekFirst
    Deque<Integer> que1;
    Deque<Integer> que2; // 辅助队列

    public MyStack() {
        que1 = new ArrayDeque<>();
        que2 = new ArrayDeque<>();
    }
    
    public void push(int x) {
        que1.addLast(x);
    }
    
    public int pop() {
        int size = que1.size();
        // 将que1导入que2 但是留下最后一个值
        size--;

        while (size-- > 0) {
            que2.addLast(que1.peekFirst());
            que1.pollFirst();
        }

        int res = que1.pollFirst();
        // 将que2对象的引用赋给了que1 此时que1 que2指向同一个队列
        que1 = que2;
        // 如果直接操作que2 que1也会收到影响 所以为que2分配一个新的空间
        que2 = new ArrayDeque<>();

        return res;
    }
    
    public int top() {
        return que1.peekLast();
    }
    
    public boolean empty() {
        return que1.isEmpty();
    }
// }

// 使用一个deque实现
class MyStack {
    // Deque 接口继承了 Queue 接口
    // 所以 Queue 中的 add、poll、peek等效于 Deque 中的 addLast、pollFirst、peekFirst
    Deque<Integer> que1;

    public MyStack() {
        que1 = new ArrayDeque<>();
    }
    
    public void push(int x) {
        que1.addLast(x);
    }
    
    public int pop() {
        int size = que1.size();
        size--;
        // 将 que1 导入 que2 ，但留下最后一个值
        while (size-- > 0) {
            que1.addLast(que1.peekFirst());
            que1.pollFirst();
        }

        int res = que1.pollFirst();
        return res;
    }
    
    public int top() {
        return que1.peekLast();
    }
    
    public boolean empty() {
        return que1.isEmpty();
    }
}

/**
 * Your MyStack object will be instantiated and called as such:
 * MyStack obj = new MyStack();
 * obj.push(x);
 * int param_2 = obj.pop();
 * int param_3 = obj.top();
 * boolean param_4 = obj.empty();
 */
```

