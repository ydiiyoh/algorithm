[leetcode2022. 将一维数组转变成二维数组](https://leetcode-cn.com/problems/convert-1d-array-into-2d-array/)

python一行代码搞定
```python
    def construct2DArray(self, original: List[int], m: int, n: int) -> List[List[int]]:
        return [original[i: i + n] for i in range(0, len(original), n)] if len(original) == m * n else []
```
