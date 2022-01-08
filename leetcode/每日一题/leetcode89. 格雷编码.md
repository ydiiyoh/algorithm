[leetcode89. 格雷编码](https://leetcode-cn.com/problems/gray-code/)

<img src="https://img-blog.csdnimg.cn/913cf9a7a4b04ce595f3ec01556e05c4.png" width="50%" align="middle"></img>

要求 n 的格雷编码，只需在 n-1 的格雷编码的基础上稍作改动即可

具体如下：

逆序遍历 n-1 的格雷编码， 将每个数加上 2^(n-1) 再添加到数组中，加法运算也可以使用位运算来做

python
```python
def grayCode(self, n: int) -> List[int]:
    res = [0,1]
    for i in range(1,n):
        for num in reversed(res):
            res.append(num+2**i)
    return res
```
