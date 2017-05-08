
Lab 5: AVL Trees
===================================
[AVLDelete]:http://www.mathcs.emory.edu/~cheung/Courses/323/Syllabus/Trees/AVL-delete.html
[AVLCheck]:https://www.cs.usfca.edu/~galles/visualization/AVLtree.html

To do the following excercises, first type into your terminal the following command:
`git clone https://github.com/Andre-Castro/cs14Spr17Week6`. You should now see a folder with a single
.h file and a single .o file.

Feel free to use the following site to double check the correctnes of your AVL Trees: [Click me!][AVLCheck] 

Exercise 1 - Remove
----------
Make a function `void remove(const string &);` that removes the node with the specified value from the tree.
**Be sure** to keep the properties of an balanced tree. 

For example, in the following tree:

![alt-text] (https://github.com/Andre-Castro/cs14Spr17Week6/blob/master/j.jpg?raw=true)

The removal of node f would look like:

![alt-text] (https://github.com/Andre-Castro/cs14Spr17Week6/blob/master/j2.jpg?raw=true)

And the subsequent remval of nodes `e` and `g` would look like:

![alt-text] (https://github.com/Andre-Castro/cs14Spr17Week6/blob/master/j3.jpg?raw=true)

For more help on AVL Tree deletions check out the following link: [AVL Tree Deletions][AVLDelete]
