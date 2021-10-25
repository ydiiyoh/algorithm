## 题目地址
[https://leetcode-cn.com/problems/search-a-2d-matrix/](https://leetcode-cn.com/problems/search-a-2d-matrix/)

## 题目描述
```
编写一个高效的算法来判断 m x n 矩阵中，是否存在一个目标值。该矩阵具有如下特性：
    每行中的整数从左到右按升序排列。
    每行的第一个整数大于前一行的最后一个整数。

示例 1：
输入：matrix = [[1,3,5,7],[10,11,16,20],[23,30,34,60]], target = 3
输出：true

示例 2：
输入：matrix = [[1,3,5,7],[10,11,16,20],[23,30,34,60]], target = 13
输出：false

提示：
    m == matrix.length
    n == matrix[i].length
    1 <= m, n <= 100
    -104 <= matrix[i][j], target <= 104
```

## 主要思路
数组元素的值从左到右，从上到下是依次递增的，因此，运用二分查找就能解决。
## 代码实现
javascript
```javascript
var searchMatrix = function(matrix, target) {
    const m = matrix.length, n = matrix[0].length;
    let l = 0, r = m*n - 1;
    while (l <= r) {
        let mid = l + r >> 1;
        if (matrix[Math.floor(mid/n)][mid%n] > target) {
            r = mid - 1;
        } else if (matrix[Math.floor(mid/n)][mid%n] < target) {
            l = mid + 1;
        } else {
            return true;
        }
    }
    return false;
};
```

