Binary Search Trees (BST)
=========

<iframe src="//giphy.com/embed/5mBE2MiMVFITS" width="480" height="319" frameBorder="0" class="giphy-embed" allowFullScreen></iframe><p><a href="http://giphy.com/gifs/paul-comment-ron-5mBE2MiMVFITS"></a></p>



What's a tree?
--------------
Trees are often easier to deal with recursively (or if you're a mathematician, 'inductively').
Thus, to define a tree recursively, we can say that:

1. A Tree is a system of **nodes**
    * A node consists of a value and pointers to its children
    * An **Internal Node** is a node with at least one child
2. Every node has a unique **parent**
    * A node with a child is said to be that child's parent
    * A node's **ancestor** include the node's parent, the parent's parent, ect., up to the tree's root
	  * No node has more than one parent
3. The **Root** of a tree has no parent
4. A Node can have any number of children (including 0)

When we put all of these things together, we end up with something looking like:

<img src="http://upload.wikimedia.org/wikipedia/commons/thumb/f/f7/Binary_tree.svg/220px-Binary_tree.svg.png" alt="It's a Tree!" style="width: 250px;"/>

Where the numbers in the nodes represent the value at that node, and the arrows represent pointers to children nodes.


Here are a few additional terms that are good to know about trees:

* The link from a node to a child is called an **edge**.
* A node's **depth** is the number of edges on the path from the root to the node. The root node thus has depth 0.
* All nodes with the same depth form a tree **level**.
* A tree's **height** is the largest depth of any node. A tree with just one node has height 0.

What's a BST?
-------------
A Binary Search Tree is exactly like any other tree, except every node has **exactly** two children (if there is no child, the node will be a null pointer).
Furtermore (and more importantly), every child to the left of a node will be less than the node, while every child to the right will be greater.

You'll notice that the picture above is **NOT** a BST. Even though each node has two children (we can pretend that there are invisible null children), if we go to the left child of our root, we find a value that is *greater*, breaking our definition.

**This** would be a valid Binary Search Tree:

<img src="http://upload.wikimedia.org/wikipedia/commons/thumb/d/da/Binary_search_tree.svg/2000px-Binary_search_tree.svg.png" alt="It's a BST!" style="width: 250px;"/>

Notice how **every** number to the left of any node (take 8 for example), is less than the node itself (1, 3, 4, 5, 7). Since this is the case, where will the smallest node be? What about the largest?



BST Searching algorithm
------------------------

Given a key, a search algorithm returns the first node found matching that key, or returns 0 if a matching node is not found. A simple BST search algorithm checks the current node (initially the tree's root), returning that node as a match, else assigning the current node with the left (if key is less) or right (if key is greater) child and repeating. If such a child is 0, the algorithm returns 0 (matching node not found).

Here's an example of how powerful a BST can be. If we have a BST and a sorted array, searching for a specific number can be much faster.


<img src="https://blog.penjee.com/wp-content/uploads/2015/11/binary-search-tree-sorted-array-animation.gif"/>



BST Insert Algorithm
----------------------
Given a new node, a BST insert operation inserts the new node in a proper location obeying the BST ordering property. A simple BST insert algorithm compares the new node with the current node (initially the root):

  * __Insert as left child:__ If the new node's key is less than the current node, and the current node's left child is 0, the algorithm assigns that node's left child with the new node.
  * __Insert as right child:__ If the new node's key is greater than the current node, and the current node's right child is 0, the algorithm assigns the node's right child with the new node.
  * __Search for insert location:__ If the left (or right) child is not 0, the algorithm assigns the current node with that child and continues searching for a proper insert location.

Here's an animated example of BST insertion:

<img src="https://blog.penjee.com/wp-content/uploads/2015/11/binary-search-tree-insertion-animation.gif"/>


BST Delete Algorithm
---------------------
Deletion in a BST is a bit tedious as compared to Insertion and searching. This is because the resultant tree after deleting a node from a BST must also be a BST (it should preserve the BST property).

Given a key, a BST remove operation removes the first-found matching node, restructuring the tree to preserve the BST ordering property. The algorithm first searches for a matching node just like the search algorithm. If found (call this node X), the algorithm performs one of the following sub-algorithms:

* __Remove a leaf node:__ If X has a parent (so X is not the root), the parent's left or right child (whichever points to X) is assigned with 0. Else, if X was the root, the root pointer is assigned with 0, and the BST is now empty.
<img src="http://www.mybodhizone.com/data_structures/images/BST_delete_no_child.gif"/>
* __Remove an internal node with single child:__ If X has a parent (so X is not the root), the parent's left or right child (whichever points to X) is assigned with X's single child. Else, if X was the root, the root pointer is assigned with X's single child.
<img src="http://www.mybodhizone.com/data_structures/images/BST_delete_one_child.gif"/>
* __Remove an internal node with two children:__ This case is the hardest. First, the algorithm locates X's successor (the leftmost child of X's right subtree), and copies the successor to X. Then, the algorithm recursively removes the successor from the right subtree.
<img src="http://www.mybodhizone.com/data_structures/images/BST_delete_two_child.gif"/>



Put it into practice!
---------------------
We have created a [simple implementation of a BST](https://gist.github.com/scohe001/65ae445a6577cb85b22c) for you to use. The class comes with the member functions `void push(T val)` to add values to the tree, and `void print()` to print a rough representation of the tree.


######NOTE:
*It is often almost always easier to write Tree functions recursively (as you'll see the push function has been written). However, it **is** possible to do all of the following exercises without recursion--you'll just need to be iterating over a stack you're constantly pushing and popping to (as you'll see the print function is doing).*
