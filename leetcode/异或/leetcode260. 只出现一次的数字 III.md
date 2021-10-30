[leetcode260. 只出现一次的数字 III](https://leetcode-cn.com/problems/single-number-iii/)
#### 主要思路
异或
#### 代码实现
```js
var singleNumber = function(nums) {
    let xor = 0;
    for (const num of nums) {
        xor ^= num;
    }
    // lsb是两个目标值异或后，保留二进制最低位1的结果。
    // 两个目标值的二进制表示在这个最低位1上的数字必然不同
    // 这样一来就可以通过 目标值&lsb 来区分两个目标值
    const lsb = xor & (-xor);
    let a = 0, b = 0;
    for (const num of nums) {
        if (num & lsb) {
            a ^= num;
        } else {
            b ^= num;
        }
    }

    return [a, b];
};
```
