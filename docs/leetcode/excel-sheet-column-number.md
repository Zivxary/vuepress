# 題目：[Excel Sheet Column Number](https://leetcode.com/problems/excel-sheet-column-number/)

Given a column title as appear in an Excel sheet, return its corresponding column number.

For example:

```
    A -> 1
    B -> 2
    C -> 3
    ...
    Z -> 26
    AA -> 27
    AB -> 28
    ...
```

### **Example 1:**

```
Input: "A"
Output: 1
```

### **Example 2:**

```
Input: "AB"
Output: 28
```

### **Example 3:**

```
Input: "ZY"
Output: 701
```

---

## 解法

### JAVA

``` java
class Solution {
    public int titleToNumber(String s) {
        int num = 0;
        for (char ch : s.toCharArray()) {
            num = num * 26 + ch - 'A' + 1;
        }
        return num;
    }
}
```

### JAVA 8 stream

``` java
class Solution {
    public int titleToNumber(String s) {
        return s.chars().reduce(0, (n, ch) -> n * 26 + ch - 'A' + 1);
    }
}
```
