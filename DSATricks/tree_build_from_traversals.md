# Reconstruct Binary Tree from Preorder and Inorder Traversals

## Problem Statement
Given two integer arrays `preorder` and `inorder` where:
- `preorder` is the preorder traversal of a binary tree (Root → Left → Right)
- `inorder` is the inorder traversal of the same tree (Left → Root → Right)

Construct and return the binary tree.

---

## Key Concepts

### Preorder Traversal
- Visits nodes in the order: **Root → Left → Right**
- The **first element** of the preorder list is always the **root** of the current subtree

### Inorder Traversal
- Visits nodes in the order: **Left → Root → Right**
- The position of the root in the inorder list splits the tree into:
  - Left subtree (elements before the root)
  - Right subtree (elements after the root)

### Recursive Construction Strategy
1. Use a global index (`preorderIndex`) to keep track of the current root node in preorder array.
2. Use a HashMap to store the value-to-index mapping of inorder elements to avoid repeated scanning.
3. Create a recursive helper that accepts:
   - `left`, `right`: the bounds of the current subtree in the inorder array
   - Use the current value from `preorder[preorderIndex]` as the root
   - Split the inorder segment using the root's index
   - Recursively construct left and right subtrees

### Why Inorder Bounds?
- Only the `inorder` array needs bounds, because it defines the structure (left and right subtree boundaries)
- The `preorder` array is traversed linearly using `preorderIndex` since it always gives the next root

---

## Java Code
```java
class Solution {
    private int preorderIndex = 0;
    private Map<Integer, Integer> inorderIndexMap;

    public TreeNode buildTree(int[] preorder, int[] inorder) {
        inorderIndexMap = new HashMap<>();
        for (int i = 0; i < inorder.length; i++) {
            inorderIndexMap.put(inorder[i], i);
        }
        return buildTreeHelper(preorder, 0, inorder.length - 1);
    }

    private TreeNode buildTreeHelper(int[] preorder, int left, int right) {
        if (left > right) {
            return null;
        }

        int rootValue = preorder[preorderIndex++];
        TreeNode root = new TreeNode(rootValue);

        int index = inorderIndexMap.get(rootValue);

        root.left = buildTreeHelper(preorder, left, index - 1);
        root.right = buildTreeHelper(preorder, index + 1, right);

        return root;
    }
}
```

---

## Optimization Tips
- Avoid slicing arrays by using index bounds
- Use a HashMap for O(1) lookup of inorder root index

---

## Dry Run Example
**preorder = [3,9,20,15,7]**  
**inorder = [9,3,15,20,7]**

- Root = 3 → Left: [9], Right: [15,20,7]
- Left Subtree: Root = 9 → Leaf
- Right Subtree: Root = 20 → Left = 15, Right = 7

---

## Summary
This approach leverages the characteristics of preorder and inorder traversal to build the tree recursively. Use `preorder` to identify roots in sequence, and `inorder` to identify subtree boundaries.
