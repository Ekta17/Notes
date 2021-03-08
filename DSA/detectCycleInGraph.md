# Detect a cycle in a graph

### **Undirected graph**

- requires to maintain a **parent property** while calling DFS. 
- so now in addition to checking the node is visited or not, we check for 
parent too.
- If the child is not visited then continue with DFS for that child 
- If a child is visited, then check if the child is the parent of the current node. 
- while calling for the first time, pass parent as -1. 
- https://www.youtube.com/watch?v=Gx-uJSqIa1Q&list=PL1w8k37X_6L9IfRTVvL-tKnrZ_F-8HJQt&index=10

**Code:** https://github.com/Ekta17/DataStructureAndAlgorithms/blob/main/src/main/java/graph/randomquestions/DetectCycleInUndirectedGraph.java



### **Directed graph**

- requires to maintain a **recursion stack** which stores values of ancestors of a node.
- like the property boolean visited, 
  maintain another boolean array as recursion stack 
- when first visiting a node, 
  mark recursion stack position as true, 
  meaning we are currently visiting this node. 
- when done visiting the node (meaning all the children of this node has been visited), 
  mark recursion stack position as false, 
  meaning we are done visiting this node.
- for each child node, call recursively isCyclic method, 
  if any call returns true then there exist a cycle.
- After visiting all the children, mark recursion stack for this current node as false.
- If no cycle as been detected so far, return false.   
- https://www.geeksforgeeks.org/detect-cycle-in-a-graph/

**Code:** https://github.com/Ekta17/DataStructureAndAlgorithms/blob/main/src/main/java/graph/randomquestions/DetectCycleInDirectedGraph.java

