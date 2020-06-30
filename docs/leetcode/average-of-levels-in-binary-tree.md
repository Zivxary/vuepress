# 題目：[Average of Levels in Binary Tree](https://leetcode.com/problems/average-of-levels-in-binary-tree)

Given a non-empty binary tree, return the average value of the nodes on each level in the form of an array.

### **Example 1:**

```
Input:
    3
   / \
  9  20
    /  \
   15   7
Output: [3, 14.5, 11]
Explanation:
The average value of nodes on level 0 is 3,  on level 1 is 14.5, and on level 2 is 11. Hence return [3, 14.5, 11].
```

### **Note:**

1. The range of node's value is in the range of 32-bit signed integer.

---

## 解法

```java
class Solution {

    List<Numbers> list = new ArrayList<>();

    public List<Double> averageOfLevels(TreeNode root) {
        putValue(root,0);
        return list.stream().map(Numbers::average).collect(Collectors.toList());//.filter(n -> n > 0)
    }

    private void putValue(TreeNode root, int depth) {
        if (root == null) {
            return;
        }
        if(list.size() <= depth ){
            list.add(new Numbers());
        }
        putValue(root.right, depth + 1);
        putValue(root.left, depth + 1);
        list.get(depth).add(root.val);
    }

    class Numbers {
        double sum = 0;
        int count = 0;

        void add(int num) {
            sum += num;
            count++;
        }
        double average() {
            if(count <= 0)
                return 0;
            return sum / count;
        }
    }
}
```
