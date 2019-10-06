---
layout: post
title: Stack, Queues, recursions
author: Thong Ho
date: '2019-2-2 21:35:23 +0530'
categories: Computer_system_enginering
summary:  stack, queue
thumbnail: siteleaf.jpg
permalink: /:categories/stack-queues-recursions
use_math: true
---

# STACKS, QUEUES, RECURSIONS

reference : book: Data structures and Algorithm in C++  (MiChael T.Goodrich - Roberto Tamassia - David Mount)

## Algorithm analysis
- Big-Oh Notation is used to characterize running times and space bound in terms of some parameter n.
- Definition: 
    - Let $f(n)$ and $g(n)$ be function mapping nonnegative intergers to real numbers. 
    - We say that $f(n)$ is $O(g(n))$ if there is a real constant c>o and an integer constant $n_0 \geq 1$, such that $f(n) < cg(n)$ for every integer $n \geq n_0$

-  Common terms used in algorithm analysis:
    - Logarithmic $O(log n)$
    - Linear $O(n)$
    - Quadratic $O(n^2)$
    - Cubic $O(n^3)$
    - Polynominal $O(n^k) (k >= 1)$
    - Exponential $O(a^n)$

    - Any algorithm runining in $O(n log n)$ time should be considered effective


    ## Recursion
    1. Linear recursion
    2. High order recursion


## Stack
- Stack is an abstract data type ((ADT)) that uses (last-in-first-out) principle
    - A physical implementation of the stack
        ![](/assets/img/computer_system_enginering/stack.JPG)
- Support functions: 
    - (push(o)): insert object o at the top of the stack.   (Input: Object; Output: None )
    - (pop()): remove from the stack and return the top on the stack; an error occurs if the stack is empty.
    - (size()): return the number of objects in the stack. (Input: None; Output: Integer)
    - (isEmpty()): return a Boolean indicating if the stack is empty. (Input: None; Output: Boolean)
    - (top()): Return the top object on the stack, without removing it; an error occurs if the stack is empty. (Input: None; Output: Object)
    - (empty()): Return true if the stack is empty and false otherwise.
- Example : 

    ![](/assets/img/computer_system_enginering/stack_ex.JPG)


## Queues
- Queue is a data structure which uses (First-in-first-out) principle: 
- The queue Abstract Data Type
    - (enqueue(o)): insert object o at the rear of the queue. 
        - (Input: Object; Output: None)
    - (dequeue()): remove and return from the queue the object at the front; an error occurs if the queue is empty. 
        - (Input: None; Output: None)
    - (size()): Return the number of the objects in the queue. 
        - (Input: None; Output: Integer)
    - (isEmpty()): return a Boolean value indicating if the queue is empty. 
        - (Input: None; Output: Boolean.)
    - (front()): return, but do not remove, a reference to the front element in the queue; an error occurs if the queue is empty. 
        - (Input: None; Output: Object).

- Example: The following table shows a series of queue operations and their effects on an initially empty queue, (Q), of intergers. 
    
    ![](/assets/img/computer_system_enginering/queue.JPG)

- The STD Queue
    - lib: 
    ```cpp
        #include <queue>
        using std::queue; // make queue accessible
        queue<float> myQueue; // a queue of floats
    ```
    - (size()): Return the number of elements in the queue.
    - (empty()): Return true if the queue is empty and false otherwise.
    - (push(e)): Enqueue e at the rear of the queue.
    - (pop()): Dequeue the element at the front of the queue.
    - (front()): Return a reference to the element at the queue’s front.
    - (back()): Return a reference to the element at the queue’s rear.

- Example 2. 
    ```cpp
    #include <iostream>
    #include <queue>
    using namespace std;
    void main() {
    queue<int> myQueue;
    myQueue.push(3);
    myQueue.push(4);
    myQueue.push(5);
    myQueue.push(6);
    cout << myQueue.size() << '\n';
    cout << myQueue.front() << '\n';
    myQueue.pop ();
    cout << myQueue.empty() << '\n';
    cout << myQueue.size() << '\n';
    getchar();
    }
    ```

## Double-Ended Queues - (Deque)
- Deque, pronounced “deck”, is a queue‐like data structure that supports insertion and deletion at both the front and the rear of the queue 
- Function of deque ADT : 
    - (insertFront(e)): Insert a new element e at the beginning of the deque.
    - (insertBack(e)): Insert a new element e at the end of the deque.
    - (eraseFront()): Remove the first element of the deque; an error occurs if the deque is empty.
    - (eraseBack()): Remove the last element of the deque; an error occurs if the deque is empty.
- Additional functions:
    - (front()): Return the first element of the deque; an error occurs if the deque is empty.
    - (back()): Return the last element of the deque; an error occurs if the deque is empty.
    - (size()): Return the number of elements of the deque.
    - (empty()): Return true if the deque is empty and false otherwise.
- Example :

    ![](/assets/img/computer_system_enginering/deque.JPG)

- STL deque
    ```cpp
    #include <deque>
    using std::deque; // make deque accessible
    deque<string> myDeque; // a deque of strings
    ```

    - (size()): Return the number of elements in the deque.
    - (empty()): Return true if the deque is empty and false otherwise.
    - (push front(e)): Insert e at the beginning the deque.
    - (push back(e)): Insert e at the end of the deque.
    - (pop front()): Remove the first element of the deque.
    - (pop back()): Remove the last element of the deque.
    - (front()): Return a reference to the deque’s first element.
    - (back()): Return a reference to the deque’s last element.