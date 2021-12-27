[825. 适龄的朋友](https://leetcode-cn.com/problems/friends-of-appropriate-ages/)

<img src="https://img-blog.csdnimg.cn/c2a05881be06439aae61c74a4801abfa.png" width="50%">

提示：
    n == ages.length
    1 <= n <= 2 * 104
    1 <= ages[i] <= 120

**方法一：暴力遍历，n^2时间复杂度**
js
```js
var numFriendRequests = function(ages) {
    let cnt = 0;
    // 将ages按从大到小排序，这样遍历的时候就满足了ages[y] <= ages[x]这个条件
    ages.sort((a,b)=>b-a);
    for (let x = 0; x < ages.length; x++) {
        for (let y = x+1; y < ages.length; y++) {
        	// 在满足所有条件的情况下，如果年龄相等，可以相互发
            if (ages[y] > 0.5 * ages[x] + 7 && !(ages[y] > 100 && ages[x] < 100)) cnt = ages[x] === ages[y] ? cnt+2 : cnt+1
        }
    }
    return cnt;
};
```

**方法二：排序+双指针**
题目给出的3个条件为：
1. ages[y] ≤ 0.5 × ages[x] + 7

2. ages[y] > ages[x]

3. ages[y] > 100 && ages[x] < 100

其中条件2包含条件3，所以如果条件2不满足的话，那条件3也不满足。
综上，只要不满足条件1和2，x 就可以给 y 发好友请求，即  **0.5×ages[x]+7<ages[y]≤ages[x]**

基于以上思路，将ages数组排序，对于ages中的每个age，用两个指针 left 和 right 来维护满足条件的
ages[y] 范围，并求和得出答案

==js==
```js
	  const n = ages.length;
    ages.sort((a, b) => a - b);
    let left = 0, right = 0, ans = 0;
    for (const age of ages) {
        // x的age<15一定不满足条件
        if (age < 15) continue;
        while (ages[left] <= 0.5 * age + 7) left++;
        while (right + 1 < n && ages[right + 1] <= age) ++right;
        // 这里要去掉x本身
        ans += right - left;
    }
    return ans;
```
**方法三：计数排序 + 前缀和**
和方法二类似思路，只不过排序方式改成**计数排序**，这样可以进一步降低时间复杂度到O(n)
相应地，统计总和的方式发生变化，采用了前缀和的方法
js
```js
	  const cnt = new Array(121).fill(0), pre = new Array(121).fill(0);
    let ans = 0;
    for (const age of ages) ++cnt[age];
    for (let i = 1; i <= 120; ++i) pre[i] = pre[i - 1] + cnt[i];
    for (let i = 15; i <= 120; ++i) {
        if (cnt[i] > 0) ans += cnt[i] * (pre[i] - pre[Math.floor(i * 0.5 + 7)] - 1);
    }
    return ans;
```



