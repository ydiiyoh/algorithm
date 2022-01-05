[leetcode1576. 替换所有的问号](https://leetcode-cn.com/problems/replace-all-s-to-avoid-consecutive-repeating-characters/)

```python
def modifyString(self, s: str) -> str:
    arr, m = list(s), len(s)
    for i in range(m):
        if arr[i] == "?":
        	# 不能有重复的字符，实际上问号的替换范围不需要从26个字母，只需从3个字母中找即可
            for j in "def":
                if not (i-1>=0 and j==arr[i-1] or i+1<m and j==arr[i+1]):
                    arr[i]=j
                    break
    return "".join(arr) 
```
