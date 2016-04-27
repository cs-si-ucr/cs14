Lab 4: Trees
===================================

Exercise 1 - Binary Search Trees
----------

Today we will be working on implementing a BST. 

We've written the foundation for a program to create a Tree, so all you have to do fill in the remaining function implementations!

_Note, since we're giving you a precompiled file, you're going to have to use C9 for this exercise_

How to get the code
-------------------
In your C9 terminal, run the following in the directory where you want the code



You'll notice you now have a `main`, and a `Tree` class.

We've already completed most of the implementation of the `Tree` class for you. The details for doing the blanks so are in the comments, so don't just delete them!

Compiling
---------

Since we're using C++11 features, you'll have to compile with the following:

	g++ -std=c++11 -Wall main.cpp Tree.cpp
	
Part 1: Printing the tree
----------
Implement the print recursive function to print all of the values of the tree in order.

```cpp
Tree test = {5, 2, 7, 3, 8, 3, 7};
print("Printing!", MAGENTA);
cout << endl;
test.print();
```

The output should look like the following:
```cpp
Printing!
2 3 5 7 8 
```

Part 2: Maximum and Minimum
----------
Implement recurisve min and max functions to find the min and max value in the tree whose root is the parameter.

```cpp
Tree test = {5, 2, 7, 3, 8, 3, 7};
Node* min = test.min();
Node* max = test.max();
cout << "Min: " << min->val << endl << "Max: " << max->val << endl;
```
The output should look like the following:
```cpp
Min: 2
Max: 8
```

Part 3: Find
----------
Implement the find recursive function to find a value in the tree and return it's node pointer (returning 0 if not found).

```cpp
Tree test = {5, 2, 7, 3, 8, 3, 7};
Node* f1 = test.find(6);
Node* f2 = test.find(7);
```
Be sure to notify the user whether or not the value is found. 

Part 4: Conversion
----------
 Implement a to_vec function that converts the tree to a vector and returns the sorted vector of tree values.
 
```cpp
Tree test = {5, 2, 7, 3, 8, 3, 7};
vector<int> v = test.to_vector();
```
The vector should contain the following values (in this order): 2 3 5 7 8

