# 題目：[N-ary Tree Preorder Traversal](https://leetcode.com/problems/n-ary-tree-preorder-traversal/description/)

Given an n-ary tree, return the preorder traversal of its nodes' values.

Nary-Tree input serialization is represented in their level order traversal, each group of children is separated by the null value (See examples).

### **Follow up:**

Recursive solution is trivial, could you do it iteratively?

### **Example 1:**

```
      1
  +---+---+
  3   2   4
+-+-+
5   6

Input: root = [1,null,3,2,4,null,5,6]
Output: [1,3,5,6,2,4]
```

### **Example 2:**

```
       1
+---+--+--+-----+
2   3     4     5
  +-+-+   |   +-+-+
  6   7   8   9   10
      |   |   |
      11  12  13
      |
      14

Input: root = [1,null,2,3,4,5,null,null,6,7,null,8,null,9,10,null,null,11,null,12,null,13,null,null,14]
Output: [1,2,3,6,7,11,14,4,8,12,5,9,13,10]
```

### **Constraints:**

- The height of the n-ary tree is less than or equal to 1000
- The total number of nodes is between [0, 10^4]

## 解法

```java
class Solution {
    public List<Integer> preorder(Node root) {
        List<Integer> list = new LinkedList<>();
        DFS(root, list);
        return list;
    }

    private void DFS(Node root, List<Integer> list) {
        if (root == null) {
            return;
        }
        list.add(root.val);
        for (Node node : root.children) {
            DFS(node, list);
        }
    }
}
```
