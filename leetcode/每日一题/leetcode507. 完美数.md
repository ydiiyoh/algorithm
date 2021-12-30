[leetcode507. 完美数](https://leetcode-cn.com/problems/perfect-number/)

<img src="https://img-blog.csdnimg.cn/8f9dfab3f5684fbebba37ad0f992ec3b.png" width="50%">

1 <= num <= 10^8

这题直接枚举就好

python
```python
    def checkPerfectNumber(self, num: int) -> bool:
        if num == 1:
            return False
        sum = 1
        for i in range(2, ceil(num**0.5)):
            if num % i == 0:
                sum += i
                if i != num/i:
                    sum += num/i 
        return sum == num   
```
