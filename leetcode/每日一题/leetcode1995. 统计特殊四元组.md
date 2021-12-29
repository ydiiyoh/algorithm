[leetcode1995. 统计特殊四元组](https://leetcode-cn.com/problems/count-special-quadruplets/)

<img src="https://img-blog.csdnimg.cn/b785b18c7cf546f086ff32d172eedfe9.png" width="50%">

从暴力枚举到哈希表到背包，一步一步降低时间复杂度

**方法一：暴力**

python
```python
n, res = len(nums), 0
for a in range(n):
    for b in range(a + 1, n):
        for c in range(b + 1, n):
            for d in range(c + 1, n):
                if nums[a] + nums[b] + nums[c] == nums[d]:
                    res += 1
return res
```
时间复杂度：O(n^4)

**方法二：哈希表**

用哈希表来存储nums[d]出现的次数

具体地，从倒数第二个数开始逆序遍历c，并在每次遍历的过程中将 c 后面一个数加到哈希表中

python
```python
        n, ans, cnt = len(nums), 0, Counter()
        for c in range(n - 2, 1, -1):
            cnt[nums[c + 1]] += 1
            for a in range(c):
                for b in range(a + 1, c):
                    if (total := nums[a] + nums[b] + nums[c]) in cnt:
                        ans += cnt[total]
        return ans
```
时间复杂度：O(n^3)

用哈希表存储 nums[d]−nums[c] 能进一步降低时间复杂度

```python
        n, ans, cnt = len(nums), 0, Counter()
        for b in range(n - 3, 0, -1):
            for d in range(b + 2, n):
                cnt[nums[d] - nums[b + 1]] += 1
            for a in range(b):
                if (total := nums[a] + nums[b]) in cnt:
                    ans += cnt[total]
        return ans
```
时间复杂度：O(n^2)

**方法三：背包动态规划**

定义 f [ i ] [ j ] [ k ] 为用前 i 个物品(数字)，凑成数值恰好为 j，使用 k 个数 的方案数。
则有状态转移方程：
```
f[i][j][k] = f[i-1][j][k] + f[i-1][j-nums[i-1]][k]
```

python
```python
		# 这里采用的是降维写法
        dp, ans = [[0] * 101 for _ in range(4)], 0
        dp[0][0] = 1
        for num in nums:
            ans += dp[3][num]
            for j in range(3, 0, -1):
                for i in range(num, len(dp[0])):
                    dp[j][i] += dp[j-1][i-num]
        return ans
```
时间复杂度：O(n)
