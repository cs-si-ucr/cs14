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


Exercise 1: Fibonacci Exercise
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


Exercise 2: Palindrome Exercise
====================
Write a program that will test to see if a specific word is a palindrome using the std::list
data structure.


* Input:	string input
* Output:	result of the palindrome test


Example:

* Enter a word to test for palindrome: <font color='red'>tacocats</font>
* <font color='red'>tacocats</font> is not a palindrome.

_Key functions to incorporate: back(), pop_back()_

Exercise 3: Animation!
==========

We've written the foundation for a program to create animations in the terminal, all you have to do is connect the dots!

At the moment, the program will push encrypted characters that need to be displayed into a queue, but those characters still need to be put into `cout`!

_Note, since we're giving you a precompiled file, you're going to have to use C9 for this exercise_

How to get the code
-------------------
In your C9 terminal, run the following in the directory where you want the code

	git clone https://github.com/scohe001/Animations

You'll notice you now have a `main`, an `Animator` class and a couple animation files (don't look at them yet, it'll ruin the surprise!<sup>[*](#myfootnote1)</sup>).

We've already completely implemented the `Animator` class for you and compiled it, so all you'll have to do is finish off the `main` skeleton! The details for doing so are in the comments, so don't just delete them!

Compiling
---------

Since we're using C++11 features and threading, you'll have to compile with the following:

	g++ -std=c++11 -pthread -Wall main.cpp animation.o

After you get your main up and running, test it out with all four animations! I'd highly suggest starting with the Eyes animation, as it's the simplest by far of all of them so it'll be easier to debug. Once you get one animation working, they should all work!

Once you have all of the animations working, delete `animation.o` and use the skeleton `animation.cpp` we've given you to complete the `Animation` class! Recompiling the `Animation` class should look like the following:

	g++ -std=c++11 -pthread -c animation.cpp



_<a name="myfootnote1">*</a> Since you're all CS majors I'm sure the lot of you have already looked at them >.>_
