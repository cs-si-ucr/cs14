
Lab 4: Binary Trees
===================================

Exercise 1- Using BST's
----------
To help you understand how a Binary Search Tree works, we've gone ahead and written a BST class which you can get by
copying and pasting the following command into your cloud 9 terminal: `git clone https://github.com/gpric001/cs14 `

After downloading the files, you will notice an empty main.cpp and BST object and header files. Using this main
template, perform the following tasks

* Insert 5 elements, `3`, `6`, `7`, `0`, `1` into the tree
* Write out the pre, in, and post order traversals of the tree and see if you got them right
* Insert 8 more elements, `4`, `5`, `2`, `8`, `9`, `10`, `11` and draw out the tree, marking where 2 should be. What is the height of this tree?
* Print out the in order traversal to see if you are correct
* Remove nodes `5`, `4`, `2`, `1`, and `0`. Do you notice anything unique about this tree? Print out a traversal of your choice to see if you are correct about the tree structure.
* What is the run time to find node `11` in this new tree?

Exercise 1.1. Num Nodes
----------
Using the provided BST code, implement a function `numNodes();` that returns the total number of nodes in the BST.

Exercise 1.2 - Depth
-----------
For this excercise, write a function `depth(Node*);` that returns the depth of the node passed in in the tree.
To review, the 'Depth' of a node is defined as the number of ancestors for any given node. In the following tree,

![alt text] (https://upload.wikimedia.org/wikipedia/commons/thumb/d/da/Binary_search_tree.svg/200px-Binary_search_tree.svg.png)

The depth of the node `3` is one since it has only one ancestor. The depth of the node `13` is 3 since it has 3 ancestors.
Keep in mind that the depth of the node `8` is indeed 0 as it has no ancestors, it is the `head` of the tree.

Exercise 1.3 - Child Swap
----------

No, this is not the latest reality TV show

![alt text](https://c1.staticflickr.com/8/7526/15949537925_21300de845_b.jpg)

Your task is to implement a function that swaps the left and right child of each node in the tree. For example, 

![alt text] (http://www.geeksforgeeks.org/wp-content/uploads/2009/06/MirrorTree1.GIF)

In the image you can see how the node `3` was once the left child of node `1` and node `2` was the right 
child of node `1`. However, after the swap we can now see that nodes `3` and `2` have switched places, 
as well as any of the other nodes in the tree (nodes `4` and `5`).

Exercise 1.4 - Tree Merge
------------
In this excercise, create a function `mergeTrees(BST one, BST two)` that takes in two BST's and 'merges' them together. That is 
to say that take all the nodes from tree one, and add them appropriately to the tree with a inorder traversal.
For example, if the tree you are trying to add looks like:

![alt text] (https://upload.wikimedia.org/wikipedia/commons/1/10/Bstreesample.jpg)

The the order of elements added should be:  `20`, `30`, `40`, `50`, `90`, `100`.
