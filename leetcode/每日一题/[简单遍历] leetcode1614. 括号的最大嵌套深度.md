[leetcode1614. 括号的最大嵌套深度](https://leetcode-cn.com/problems/maximum-nesting-depth-of-the-parentheses/)
```python
def maxDepth(self, s: str) -> int:
    cur = res = 0
    for i in s:
        if i == "(":
            cur += 1
            res = max(cur, res)
        if i == ")":
            cur -= 1
    return res
```

