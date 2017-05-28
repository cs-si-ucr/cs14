Breadth First Search (BFS)
==========================
Just when you thought you were done with traverls after post, in and preorder, here are two more!! (For graphs).
But don't fret, they are not that conceptually difficult.

The first graph traversal you will learn about is "Breadth First Search" or `BFS` for short. BFS starts with a
node in the graph, and traverses the graph by visiting all the nodes the shortest distance away first.
Distance from a node to another node in graphs is the amount of edges between such nodes. Consider a BST with 
the values 8, 7, and 6 inserted in that order (recall that a tree is just a unique type of graph). Starting at
node 8, the amount of edges from node 8 to node 7 would be 1, making node 7 a distance of 1 away from node 8. 
Node 6 on the other hand would be a distance of 2 away from node 8. Therefore, the BFS traversal of this BST
would look like `8,7,6` since we started at node 8 and then visited the nodes closest next.

If there are multiple nodes the same distance away, the order in which they are visited does not matter. So 
a BST with values 8,7,6,9 inserted in that order would have nodes 9 and 7 both a distance of `1` away from node 8.
However in the traversal of this tree, the results `8,7,9,6` and `8,9,7,6` are both valid BFS-es.  

Consider the following graph:

![alt-text]:(http://www.thecshandbook.com/public_html/img/uploads/graph.png)

What would the BFS traversal of this graph look like if we started from node `1`? 

Depth First Search (DFS)
========================

Djikstra's Algorithm
====================
