
# 🌳 Binary Tree Traversal Cheat Sheet

## ✅ Recursive DFS Template

### When to Use:
Use when:
- You need to **explore all paths**
- The answer **depends on values from subtrees**
- You're calculating:
  - Max/Min Depth
  - Sum of paths
  - Node counts
  - Validations (e.g., BST rules)

### Template:
```java
ReturnType dfs(TreeNode node) {
    if (node == null)
        return baseCaseValue;

    ReturnType left = dfs(node.leftChild);
    ReturnType right = dfs(node.rightChild);

    return combine(left, right, node);
}
```

### Example: Max Depth of Binary Tree
```java
int maxDepth(TreeNode root) {
    if (root == null) return 0;

    int leftDepth = maxDepth(root.leftChild);
    int rightDepth = maxDepth(root.rightChild);

    return Math.max(leftDepth, rightDepth) + 1;
}
```

### Common DFS Patterns:
| Problem | Return Type | Combine Step |
|--------|-------------|--------------|
| Max Depth | `int` | `Math.max(left, right) + 1` |
| Path Sum Exists | `boolean` | `left || right` |
| Sum of Paths | `int` | `left + right` |
| Validate BST | `boolean` | check node.val ∈ (min, max) |
| Find All Paths | `void` | backtrack & collect paths |

---

## ✅ Iterative DFS (Using Stack)

### Template:
```java
void iterativeDFS(TreeNode root) {
    if (root == null) return;

    Stack<TreeNode> stack = new Stack<>();
    stack.push(root);

    while (!stack.isEmpty()) {
        TreeNode node = stack.pop();
        // Process node

        if (node.rightChild != null) stack.push(node.rightChild);
        if (node.leftChild != null) stack.push(node.leftChild);
    }
}
```

---

## ✅ BFS (Using Queue)

### When to Use:
Use when:
- You need to process nodes **level by level**
- You need shortest path, distance, or views (left/right)

### Template:
```java
void bfs(TreeNode root) {
    if (root == null) return;

    Queue<TreeNode> queue = new LinkedList<>();
    queue.offer(root);

    while (!queue.isEmpty()) {
        int levelSize = queue.size();
        for (int i = 0; i < levelSize; i++) {
            TreeNode node = queue.poll();
            // Process node
            if (node.leftChild != null) queue.offer(node.leftChild);
            if (node.rightChild != null) queue.offer(node.rightChild);
        }
    }
}
```

---

## 🧠 Tips
- DFS is often **postorder** in recursive problems.
- BFS is ideal for **level traversal**, **views**, and **shortest path**.
- Use **print statements** to trace recursion or queue/stack contents during debugging.

