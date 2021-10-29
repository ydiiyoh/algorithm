[leetcode869. 重新排序得到 2 的幂](https://leetcode-cn.com/problems/reordered-power-of-2/)

#### 主要思路
将要判断的数字转换成字符串并排序，
判断其是否在1到1e9之间所有是2的幂的数字转换成的字符串（该字符串要排序）中

#### 代码实现
javascript
```js
var reorderedPowerOf2 = function(n) {
    const sortNum = num => (num+'').split('').sort((a,b)=>a-b).join('');
    const set = new Set();
    for (let i = 1; i <= 1e9; i<<=1) set.add(sortNum(i));
    return set.has(sortNum(n));
};
```
python
```python
        return ''.join(sorted(str(n))) in {"1", "2", "4", "8", "16", "23", "46", "128", "256", "125", "0124", "0248", "0469", "1289", "13468", "23678", "35566", "011237", "122446", "224588", "0145678", "0122579", "0134449", "0368888", "11266777", "23334455", "01466788", "112234778", "234455668", "012356789", "0112344778"}
```
