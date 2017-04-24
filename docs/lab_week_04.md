
Lab 4: Binary Trees
===================================

Exercise 1- Using BST's
----------
To help you understand how a Binary Search Tree works, we've gone ahead and written a BST class which you can get by
copying and pasting the following command into your cloud 9 terminal: `git clone https://github.com/gpric001/cs14 `

After downloading the files, you will notice an empty main.cpp and BST object and header files. Using this main
template, perform the following tasks

*

When creating the underlying array, feel free to set a max size of the array like so:
`int arr[10]; // Max Queue size`


Exercise 1.1. Num Nodes
----------
Using the provided BST code, implement a function `numNodes();` that returns the total number of nodes in the BST.

Exercise 1.2 - Depth
-----------
For this excercise, write a function `depth(Node*);` that returns the depth of the node passed in in the tree.

Exercise 1.3 - Child Swap
----------

No, this is not the latest reality TV show

![alt text](https://d1b10bmlvqabco.cloudfront.net/attach/j129btc6ipp515/h7ks2ibk8jg6s3/j1hydurqd650/Queues.pdf)

Your task is to implement a function that swaps the left and right child of each node in the tree. For example, 
![alt text] (http://www.geeksforgeeks.org/wp-content/uploads/2009/06/MirrorTree1.GIF)
In the image you can see how the node `3` was once the left child of node `1` and node `2` was the right 
child of node `1`. However, after the swap we can now see that nodes `3` and `2` have switched places, 
as well as any of the other nodes in the tree (nodes `4` and `5`).
