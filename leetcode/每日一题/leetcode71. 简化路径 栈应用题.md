[leetcode71. 简化路径](https://leetcode-cn.com/problems/simplify-path/)
```python
def simplifyPath(self, path: str) -> str:
    names = path.split("/")
    stack = list()
    for name in names:
    	# name有"" , ".." , "." 和其他这四种情况
        if name == "..": 
            if stack:
                stack.pop()
        elif name and name != ".":
            stack.append(name)
    return "/" + "/".join(stack)
```
