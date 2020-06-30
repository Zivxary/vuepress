# 題目：[Two Sum IV - Input is a BST](https://leetcode.com/problems/two-sum-iv-input-is-a-bst)

Given a Binary Search Tree and a target number, return true if there exist two elements in the BST such that their sum is equal to the given target.

### **Example 1:**

```
Input:
    5
   / \
  3   6
 / \   \
2   4   7

Target = 9

Output: True
```

### **Example 2:**

```
Input:
    5
   / \
  3   6
 / \   \
2   4   7

Target = 28

Output: False
```

---

## 解法

```java
class Solution { 
    
    
    public boolean findTarget(TreeNode root, int k) {
        Set<Integer> set = new HashSet<>();
        setPutAll(set, root);
        //再遍歷一遍，如果set內有diff
        //且diff與num不同，即return true
        for(Integer num : set) {
            int diff = k - num;
            if (set.contains(diff) && num != diff) {
                return true;
            }
        }
        return false;
    }
    
    //先把Tree所有節點存入Set
    //因為是Binary Search Tree，所以不會有重複的
    private void setPutAll(Set<Integer> set, TreeNode root) {
        if (root == null) {
            return;
        }
        set.add(root.val);
        setPutAll(set, root.left);
        setPutAll(set, root.right);
    }
}
```
