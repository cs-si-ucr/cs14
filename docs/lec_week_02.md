Lecture 2: Lists
=======================================

Question of the day!
---------------------
> How many programmers does it take to change a light bulb?
>>>> None. That's a hardware problem.

Lists
------
An **abstract data type (ADT)** is a data type described by pre-defined user operations, such as "insert data at rear," without indicating how each operation is implemented.

Lists are a common ADT for holding data, with operations like appending a data item, removing a data item, searching and printing. Each item in a list ADT is called a **node**.


Singly-linked Lists
-------------------

Singly-linked lists is a data structure for implementing a list ADT, where each node has a data and a pointer to the next node. The list structure typically has pointers to the list's first node and last node. The list's first node is called the **head**, and the last node is the **tail**.

![alt text](https://upload.wikimedia.org/wikipedia/commons/thumb/6/6d/Singly-linked-list.svg/408px-Singly-linked-list.svg.png)
	The head in this case would be the node with value 12 and the tail would be the node with value 37

In order to implement a Linked List, you must define the structure
for an individual node.

For a singly-linked list of integers, it may look something like:
```cpp
struct IntNode{
    int val;
    IntNode* next;
};
```
In order to implement the Linked List, we store the head of the list,
which is a pointer to a `IntNode`. We also implement methods that
insert/remove elements from the list
e.g.
```cpp
class IntLinkedList {
    public:
        void push_front(int val);
        // ...
    private:
        IntNode* head;
	IntNode* tail;
};
```


Doubly Linked List
------------------
In a doubly linked list, each node contains three parts:

* Data
* Pointer to the next node
* Pointer to the previous node

![alt text](https://upload.wikimedia.org/wikipedia/commons/thumb/5/5e/Doubly-linked-list.svg/610px-Doubly-linked-list.svg.png)

In this case, our new struct may look something like:
```cpp
struct IntNode{
	int val;
	IntNode* next;
	IntNode* previous;
};
```


Fibonacci Exercise
====================

Fn = Fn-1 + Fn-2

F0 = 0, F1 = 1

Write a program that will calculate a specified fibonacci number using the `std::list data`
structure. Think about how to use a list to store values of the formula above.


* Input:	integer n
* Output:	nth Fibonacci number


Example:

* Which Fibonacci number to calculate: <font color='red'>10</font>
* 10th Fibonacci number: <font color='red'>55</font>


Palindrome Exercise
====================
Write a program that will test to see if a specific word is a palindrome using the std::list
data structure.


* Input:	string input
* Output:	result of the palindrome test


Example:

* Enter a word to test for palindrome: <font color='red'>tacocats</font>
* <font color='red'>tacocats</font> is not a palindrome.

_Key functions to incorporate: back(), pop_back()_
