
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


## 🌟 Tricks to Remember: Key Tree Problems

### 🔁 Symmetric Tree (Mirror Check)

**Problem**: [Symmetric Tree](https://leetcode.com/problems/symmetric-tree/)

#### 🔑 Key Idea:
Use BFS with a queue of **node pairs** to compare left and right subtree nodes in mirror order.

#### 🧠 Tricks:
- Enqueue two nodes at a time
- Compare `left.value == right.value`
- Enqueue their children in **mirrored order**:
  - `left.leftChild` with `right.rightChild`
  - `left.rightChild` with `right.leftChild`

#### ✅ Template:
```java
Queue<TreeNode> q = new LinkedList<>();
q.add(root.leftChild);
q.add(root.rightChild);

while (!q.isEmpty()) {
    TreeNode left = q.poll();
    TreeNode right = q.poll();

    if (left == null && right == null) continue;
    if (left == null || right == null || left.value != right.value) return false;

    q.add(left.leftChild);
    q.add(right.rightChild);
    q.add(left.rightChild);
    q.add(right.leftChild);
}
```

---

### 🌲 Height-Balanced BST from Sorted Array

**Problem**: [Convert Sorted Array to Height Balanced BST](https://leetcode.com/problems/convert-sorted-array-to-binary-search-tree/)

#### 🔑 Key Idea:
Use **Divide and Conquer**: pick the middle element as root, build left/right trees recursively.

#### 🧠 Tricks:
- Always pick `mid = (left + right) / 2` as root
- Recurse left half → left subtree
- Recurse right half → right subtree
- This is **DFS-style construction**, similar to **postorder**: build children before returning parent

#### ✅ Template:
```java
TreeNode sortedArrayToBST(int[] nums) {
    return build(nums, 0, nums.length - 1);
}

TreeNode build(int[] nums, int left, int right) {
    if (left > right) return null;
    int mid = left + (right - left) / 2;

    TreeNode root = new TreeNode(nums[mid]);
    root.leftChild = build(nums, left, mid - 1);
    root.rightChild = build(nums, mid + 1, right);
    return root;
}
```
