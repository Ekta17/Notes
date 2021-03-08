# Tree Creation

### Convert Sorted Array to Binary Search Tree

- Given an array where elements are sorted in ascending order,
  convert it to a height balanced BST.
- For this problem, a height-balanced binary tree is defined as 
  a binary tree in which the depth of the two subtrees 
  of every node never differ by more than 1.
- To construct a tree, calculate the mid point of the array, 
  as this is where the elements smaller than mid will be on 
  left subtree and elements greater than mid will be on
  right subtree. 
- recursively call the function to construct BST for left and
  right subtrees 
- https://leetcode.com/explore/featured/card/top-interview-questions-easy/94/trees/631/

**Code:** https://github.com/Ekta17/DataStructureAndAlgorithms/blob/main/src/main/java/trees/binarytree/randomQuestions/TreeCreation/ConvertArrayToBST.java
