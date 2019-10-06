---
layout: post
title: Lists and Vectors, Sequences
author: Thong Ho
date: '2019-10-4 05:35:23 +0530'
categories: Computer_system_enginering
summary:  list, vector, ...
thumbnail: siteleaf.jpg
permalink: /:categories/list-iterator
use_math: true
---

## Vectors
- A vector, also called an (Array List), is an ADT that supports the following fundamental functions 
    - in addition to the standard size() and empty() functions
- A vector is an ADT that supports the following fundamental functions: 
    - (at(i)): Return the element of V with index i; an error condition occurs if i is out of range.
    - (set(i, e)): Replace the element at index i with e; an error condition occurs if i is out of range.
    - (insert(i, e)): Insert a new element e into V to have index i; an error condition occurs if i is out of range.
    - (erase(i)): Remove fromV the element at index i; an error condition occurs if i is out of range.
- Example: Some operations on an initially empty vector V

![](/assets/img/computer_system_enginering/vector1.JPG)

- STL vector class

![](/assets/img/computer_system_enginering/vector_stl.JPG)


## List
- Using an index is not the only means of referring to the place where an element
appears in a list. If we have a list L implemented with a (singly or doubly) linked
list, then it could possibly be more natural and efficient to use a node instead of an
index as a means of identifying where to access and update a list. 

- List is an ADT which supports the following functions:
    - (begin()): return the position of the first element of S
        - Input: None; Output: Position
    - (end()): return the position of the last element of S
        - Input: None; Output: Position
    - (insertFront(e)): Insert a new element e into S as the first element
        - Input: Object e; Output: None
    - (insertBack(e)): Insert a new element e into L as the last element
        - Input: Object e; Output: None
    - (insert(p,e)): Insert a new element e into L before position p in L.
        - Input: Object e, position p; Output: None
    - (eraseFront()): Remove the first element of L.
        - Input: None; Output: None
    - (eraseBack()): Remove the last element of L.
        - Input: None; Output: None
    - (erase(p)): Remove from L the element at position p; invalidates p as a position.
        - Input: None; Output: None

- Example :

    ![](/assets/img/computer_system_enginering/list1.JPG)


## Sequences 
- The Sequence ADT is a basic, general purpose, data structure for storing an ordered collection of elements
- Direct applications:
    - Generic replacement for stack, queue, vector, or list small database (e.g., address book)
- Indirect applications:
    - Building block of more complex data structures



## EXAMPLES
1. List
    ```cpp
    #include <iostream>
    #include <list>
    using namespace std;
    void main() {
    list <int> L1,L2;
    list <int>::iterator L1_Iter;
    L1.push_front(5);
    L1.push_back(10);
    L1.push_front(8);
    L1.push_back(2);
    L1.pop_front();
    L1.push_back(1);
    L2.push_back( 10 );
    L2.push_back( 20 );
    cout << "The original list L1 is:";
    for ( L1_Iter = L1.begin( ); L1_Iter != L1.end( ); L1_Iter++ )
    cout << " " << *L1_Iter;
    cout << endl;
    L1.swap(L2);
    cout << "After swapping with L2, list L1 is:";
    for ( L1_Iter = L1.begin( ); L1_Iter != L1.end( ); L1_Iter++ )
    cout << " " << *L1_Iter;
    cout << endl;
    getchar();
    }
    ```