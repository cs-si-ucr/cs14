AVL Trees
=================


An __AVL tree__ is a BST with a height balanced property and specific operations to rebalance the tree when a node is inserted or removed. A BST is __height balanced__ if for any node, the heights of the node's left and right subtrees differ by only 0 or 1/

A node's __balance factor__ is the left subtree height, which is 1, 0, or -1 in an AVL tree.

**Note**: Recall that a tree (or subtree) whith just one node has a height of 0. For calculating a balance factor, a non-existent left or right child's subtree's height is said to be -1.


Example of an AVL tree:
<img src="https://upload.wikimedia.org/wikipedia/commons/thumb/0/06/AVLtreef.svg/1920px-AVLtreef.svg.png"/>



AVL Rotations
-------------------

Inserting an item into an AVL tree may require rearranging the tree to maintain height balance. A __rotation__ is a local rearrangement of a BST that maintains the BST ordering property while rebalancing the tree.


Here are some examples of rotations:
```cpp
/* Rotates at node D as follows.

      D               B
     /    ==>       /   \
    B              A     D
   /
  A




      D               B
     /    ==>       /   \
    B              A     D
   /  \                 /
  A    C               C



                                         P             P
                                         |             |
     D         B                         D             B
    /    ==>    \    Shown w/ possible  / \    ==>    / \
   B             D   subtrees/parent:  B   T4        T1  D
    \           /                     / \               / \
     C         C                     T1  C             C   T4
                                        / \           / \
                                       T2 T3         T2 T3
*/
```



AVL Insertions
----------------------

Inserting an item into an AVL tree may cause the tree to become unbalanced. A rotation can rebalance the tree.


```cpp
/* Adding A to the tree

      D                       D
     / \       ==>           / \
    B   E                   B   E
   /                       /
  C                       C
                         /
                        A

But now the tree is unbalanced

A rotation at the problem node closest to the new node restores balance

Lets rotate at node C:


            D                           D
           / \                         / \
          C   E      ==>              B   E
         /                           / \
        B                           A  C
       /
      A
*/
```




Sometimes, the imbalance is due to an insertion on the inside of a subtree, rather than on the outside as above. One rotation won't rebalance. A double rotation is needed.

![alt text](https://upload.wikimedia.org/wikipedia/commons/thumb/f/f5/AVL_Tree_Rebalancing.svg/350px-AVL_Tree_Rebalancing.svg.png "Pictorial description of how rotations rebalance a node in AVL tree. The numbered circles represent the nodes being rebalanced. The lettered triangles represent subtrees which are themselves balanced AVL trees. A blue number next to a node denotes possible balance factors (those in parentheses occurring only in case of deletion).")

(Put your cursor over the picture to see a description!)




 After inserting a node, nodes on the path from the new node to the root should be checked for a balance factor of 2 or -2. The first such node p triggers rebalancing. Four cases exist, distinguishable by the balance factor of node p and a child.


 There are four possible imbalance cases. The red numbers are node balance factors. The rotations done are indicated by the blue arrows.

 <img
 src = "https://zytools.zybooks.com/zyAuthor/DataStructures/11/IMAGES/embedded_image311_wILEoF3aexLUPGbWmT7ydZotXfN7ys96b9_Wisp2hw_10_HLlcyVneBM.png" />



AVL Deletion
---------------


 AVL deletions can also cause problems with balance.

![alt text](https://upload.wikimedia.org/wikipedia/commons/thumb/4/46/Binary_search_tree_delete.svg/640px-Binary_search_tree_delete.svg.png "Deleting a node with two children from a binary search tree using the in-order predecessor (rightmost node in the left subtree, labelled 6).")

 Consider an arbitrary tree: Let node X be the node with the value we need to delete, and let node Y be a node in the tree we need to find to take node X's place, and let node Z be the actual node we take out of the tree.

Steps to consider when deleting a node in an AVL tree are the following:

  1. If node X is a leaf or has only one child, skip to step 5 with Z:=X.
    Otherwise, determine node Y by finding the largest[citation needed] node in node X's left subtree (the in-order predecessor of X − it does not have a right child) or the smallest in its right subtree (the in-order successor of X − it does not have a left child).
  2. Exchange all the child and parent links of node X with those of node Y. In this step, the in-order sequence between nodes X and Y is temporarily disturbed, but the tree structure doesn't change.
  3. Choose node Z to be all the child and parent links of old node Y = those of new node X.
  4. If node Z has a subtree (which then is a leaf), attach it to Z's parent.
  5. If node Z was the root (its parent is null), update root.
  6. Delete node Z.
  7. Retrace the path back up the tree (starting with node Z's parent) to the root, adjusting the balance factors as needed.




Resoucres
-----------------

[AVL Tree Simulation](https://www.cs.usfca.edu/~galles/visualization/AVLtree.html)
