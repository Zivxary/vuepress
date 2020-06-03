# 題目：[Invert Binary Tree](https://leetcode.com/problems/invert-binary-tree/description/)

Invert a binary tree.

### **Example:**

Input:
```
     4
   /   \
  2     7
 / \   / \
1   3 6   9
```
Output:
```
     4
   /   \
  7     2
 / \   / \
9   6 3   1
```
---
## 解法
``` java
class Solution {
    public TreeNode invertTree(TreeNode root) {
        if (root == null) {
            return null;
        }
        TreeNode tmpNode = root.left;
        root.left = root.right;
        root.right = tmpNode;
        invertTree(root.left);
        invertTree(root.right);
        return root;
    }
}
```