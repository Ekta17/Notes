# Tips and Tricks for Ancestor Questions in Binary Trees

Ancestor-related problems are common in technical interviews. Here’s a structured guide to help you understand, approach, and solve these problems.

---

## 1. **Find All Ancestors of a Node**

### ✅ Use Case:

Return a list of all ancestors from root to the parent of the given node.

### 💡 Tips:

- Use a recursive DFS approach.
- Track the path while backtracking after finding the target.
- Use a list to store ancestors in reverse (from bottom-up) and reverse it if needed.

### 🔁 Pattern:

```java
boolean findAncestors(TreeNode root, int target, List<Integer> ancestors) {
    if (root == null) return false;
    if (root.val == target) return true;

    if (findAncestors(root.left, target, ancestors) ||
        findAncestors(root.right, target, ancestors)) {
        ancestors.add(root.val);
        return true;
    }
    return false;
}
```

---

## 2. **Find Lowest Common Ancestor (LCA)**

### ✅ Use Case:

Find the lowest (deepest) node that is an ancestor of two given nodes `p` and `q`.

### 💡 Tips:

- Recursively check left and right subtree.
- If both sides return non-null, current node is the LCA.
- If one side is null, return the non-null side.

### 🔁 Pattern:

```java
TreeNode lowestCommonAncestor(TreeNode root, TreeNode p, TreeNode q) {
    if (root == null || root == p || root == q) return root;

    TreeNode left = lowestCommonAncestor(root.left, p, q);
    TreeNode right = lowestCommonAncestor(root.right, p, q);

    if (left != null && right != null) return root;
    return (left != null) ? left : right;
}
```

### ⚠️ Common Pitfalls:

- Forgetting to handle base cases (null root or root equals p/q).
- Confusing LCA with node value instead of reference.

---

## 3. **Find Immediate Parent of a Node**

### ✅ Use Case:

Find the direct parent of a given node.

### 💡 Tips:

- Use DFS to check if current node’s left or right child is the target.
- Otherwise, recursively search both subtrees.

### 🔁 Pattern:

```java
TreeNode findParent(TreeNode root, TreeNode target) {
    if (root == null || root == target) return null;

    if (root.left == target || root.right == target) return root;

    TreeNode left = findParent(root.left, target);
    if (left != null) return left;

    return findParent(root.right, target);
}
```

---

## 🔑 General Techniques

- **Recursive Backtracking**: Essential for problems involving ancestry/path tracing.
- **State Propagation**: Return useful info (boolean or TreeNode) up the recursion.
- **Null Checks**: Always protect against null pointers.
- **Edge Cases**: Consider root is target, or one node is ancestor of another.

---

## 🔁 Practice Problems

- Leetcode 236: Lowest Common Ancestor of a Binary Tree
- Leetcode 1123: Lowest Common Ancestor of Deepest Leaves
- Leetcode 1485: Clone Binary Tree With Random Pointer (Advanced ancestry + pointer tracking)
- Leetcode 1026: Maximum Difference Between Node and Ancestor

---

This guide should help you confidently tackle any ancestor-related binary tree question!

