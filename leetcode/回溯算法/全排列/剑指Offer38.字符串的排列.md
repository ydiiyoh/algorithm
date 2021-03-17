## 题目地址
https://leetcode-cn.com/problems/zi-fu-chuan-de-pai-lie-lcof/

## 题目描述
```
输入一个字符串，打印出该字符串中字符的所有排列。
你可以以任意顺序返回这个字符串数组，但里面不能有重复元素。
示例:
输入：s = "abc"
输出：["abc","acb","bac","bca","cab","cba"]
限制：
1 <= s 的长度 <= 8
```
## 代码实现
javascript
```
/**
 * @param {string} s
 * @return {string[]}
 */
var permutation = function(s) {
    let set = new Set();
    let obj = {};
    
    function dfs(str) {
        if (str.length === s.length) {
            set.add(str);
            return;
        }
        for (let i = 0; i < s.length; i++) {
            if (obj[i]) continue;
            obj[i] = true;
            dfs(str+s[i]);
            obj[i] = false;
        }
    }
    
    dfs('');
    return [...set];
};
```
