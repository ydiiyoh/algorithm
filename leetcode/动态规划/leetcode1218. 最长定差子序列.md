[1218. 最长定差子序列](https://leetcode-cn.com/problems/longest-arithmetic-subsequence-of-given-difference/)
#### 主要思路
动态规划

#### 代码实现
方法一
定义dp数组为：dp[i]是以arr[i]结尾的最长定差子序列的长度
javascript
```js
var longestSubsequence = function(arr, difference) {
    const dp = new Array(arr.length).fill(1);
    let res = 1;
    dp[0] = 1;
    for (let j = 1; j < arr.length; j++) {
        for (let i = 0; i < j; i++) {
            if (arr[j]-arr[i] === difference) {
                dp[j] = Math.max(dp[j], dp[i]+1);
            }
        }
        res = Math.max(res, dp[j]);
    }  
    return res;
};
```
方法二
dp[v]是以v结尾的最长定差子序列的长度
```python
class Solution:
    def longestSubsequence(self, arr: List[int], difference: int) -> int:
        dp = defaultdict(int)
        for v in arr:
            dp[v] = dp[v-difference] + 1
        return max(dp.values())
```


