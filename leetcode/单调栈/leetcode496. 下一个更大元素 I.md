[496. 下一个更大元素 I](https://leetcode-cn.com/problems/next-greater-element-i/)

## 主要思路
利用**栈**结构, 从结尾开始遍历一遍nums2，就可以知道nums2中每个元素的下一个更大元素。

## 代码实现

```javascript
	// map的key是数组元素，value是该数组元素对应的下一个更大元素，没有则为-1
    const map = new Map(), stack = [];
    for (let i = nums2.length - 1; i >= 0; --i) {
        const num = nums2[i];
        while (stack.length && num >= stack[stack.length - 1]) {
            stack.pop();
        }
        map.set(num, stack.length ? stack[stack.length - 1] : -1);
        stack.push(num);
    }
    // 下面这句是不是类似python中的列表表达式，也可以一行搞定
    return new Array(nums1.length).fill(0).map((_, i) => map.get(nums1[i]));
```
