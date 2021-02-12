# Tree Traversal

### Breadth First or Level order traversal

- In this traversal, the nodes are visited in the order --> Root -> Left subtree -> Right subtree
- Main trick is to use a queue in this traversal
- Keep adding nodes to queue, starting root node, iterate till queue is empty. poll the front of the queue, visit the children of this node recently polled if they are not null.
- Since this is a tree traversal, we know there wont be any cycles, so we dont check for isVisited flag and for a binary tree, we just need to check for children, left child and right child and if not null, add them to queue.

#### **Level Order printing of tree nodes**

- In this the modification from the standard BFS is when inside the while loop 
  (queue not empty), first fetch the size of current queue and 
  then while visiting the front of the queue, you need to visit only 
  current size number of elements from the queue.

### Depth First Traversal

- There are three forms of depth first traversal:
  - **PreOrder**: Root --> Left --> Right 
  - **InOrder**: Left --> Root -->  Right
  - **PostOrder**: Left --> Right --> Root

- In this traversal, we recursively iterate through each node in the tree
and visit one branch completely before moving to another branch of the tree.
- In a tree, dfs traversal is easier than a graph and can be achieved by simply 
traversing the tree starting from root and then following any of the three traversal
  techniques. If dont have to worry about non-connected nodes and cycles as in a tree 
  all the nodes are connected and there are no cycles. 
  
