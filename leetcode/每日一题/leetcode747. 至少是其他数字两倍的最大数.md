[leetcode747. 至少是其他数字两倍的最大数](https://leetcode-cn.com/problems/largest-number-at-least-twice-of-others/)

<img src="https://img-blog.csdnimg.cn/21a124aecbfa42bdad4a102ac3ca1842.png" width="50%"></img>


找到最大值和次大值，如果最大值至少是次大值的两倍，那其他数字肯定也符合要求

python
```python
    def dominantIndex(self, nums: List[int]) -> int:
        m1 = m2 = idx = 0
        for i, num in enumerate(nums):
            if num > m1:
                m1, m2, idx = num, m1, i
            elif num > m2:
                m2 = num
        return idx if m1 >= m2 * 2 else -1
```

