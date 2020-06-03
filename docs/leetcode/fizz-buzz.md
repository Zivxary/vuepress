# 題目：[Fizz Buzz](https://leetcode.com/problems/fizz-buzz/)

Write a program that outputs the string representation of numbers from 1 to n.

But for multiples of three it should output “Fizz” instead of the number and for the multiples of five output “Buzz”. For numbers which are multiples of both three and five output “FizzBuzz”.

### **Example:**

```
n = 15,

Return:
[
    "1",
    "2",
    "Fizz",
    "4",
    "Buzz",
    "Fizz",
    "7",
    "8",
    "Fizz",
    "Buzz",
    "11",
    "Fizz",
    "13",
    "14",
    "FizzBuzz"
]
```

---

## 解法

```java
class Solution {
    public List<String> fizzBuzz(int n) {
        List<String> list = new ArrayList<String>(n);
        IntStream
            .range(1, n+1)
            .forEach(i -> {
                if (i % 15 == 0)
                    list.add("FizzBuzz");
                else if( i%5 == 0)
                    list.add("Buzz");
                else if (i%3 == 0)
                    list.add("Fizz");
                else
                    list.add(i+"");
            });
        return list;
    }
}
```
