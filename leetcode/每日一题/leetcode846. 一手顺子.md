[leetcode846. 一手顺子](https://leetcode-cn.com/problems/hand-of-straights/)

<img src="https://img-blog.csdnimg.cn/15622101babc4c6486c4c7a373ed5d5b.png" width="50%">

####  主要思路
首先，根据 groupSize 判断手中的牌数是否能够被平分，如不能的话返回False

在满足平分条件的基础上，找出牌中数字最小的牌，判断其后的 groupSize - 1 个数字是否存在，

如此循环，直到没有牌为止

python
```python
        if len(hand) % groupSize != 0:
            return False
        hand.sort()
        cnt = Counter(hand)
        for x in hand:
            if cnt[x] == 0:
                continue
            for num in range(x, x + groupSize):
                if cnt[num] == 0:
                    return False
                cnt[num] -= 1
        return True
```
