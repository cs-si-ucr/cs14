Lab Week 7: Hash Tables
=========================

The following exercises require some code we have written. Execute the following
command on c9 (or on the terminal) to get it.

`git clone https://github.com/gpric001/cs14`

You should now have a directory called cs14/w7 with the following files: 
*Person.h*, *UnorderedSet.h*, *UnorderedSet.cpp*, *main.cpp*, and *persondata.txt*.

The *Person.h* file contains the Actor struct which has a variety of fields.
The *UnorderedSet.h* file contains the basic interface of the UnorderedSet class.
The *UnorderedSet.cpp* file is where you will be implmenting the UnorderedSet
class.
The *main.cpp* file is where you should write your tests. Right now it simply
loads the person data into a vector.
The *persondata.txt* file contains the raw person data

Exercise 1
----------

Our goal in this exercise is to implement an ADT that uses the ideas in class to
hash Person structs. Hopefully we can attain O(1) insert and remove operations.

Using the UnorderedSet class declartion in UnorderedSet.h, implement the the
UnorderedSet class. Feel free to modify UnorderedSet.h but your implementation 
of the UnorderedSet class must at least support the following public member
functions:

```cpp
int count(const Person& elem)
void remove(const Person& elem) 
void insert(const Person& elem)
```

Review the files given for hints on how to implement this class. As always,
if you are having trouble ask your neighbor or the SI leader for help.

Exercise 2
----------

Write a test for your UnorderedSet class that reports how the elements are 
distributed in your set. One way to do this is to sum the total number of
elements in each bucket and divide by the total number of buckets that have at
least one element.

If you use the above suggestion, what kind of output do you want to see for your
test?

Exercise 3
----------

Implement the `resize()` public member function. `resize()` should double the 
number of buckets if the load factor goes above a certain threshold. Do some
quick research online to determine an appropriate load factor threshold.
