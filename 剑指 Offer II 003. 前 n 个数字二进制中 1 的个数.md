给定一个非负整数 n ，请计算 0 到 n 之间的每个数字的二进制表示中 1 的个数，并输出一个数组。

 

示例 1:

输入: n = 2
输出: [0,1,1]
解释: 
0 --> 0
1 --> 1
2 --> 10
示例 2:

输入: n = 5
输出: [0,1,1,2,1,2]
解释:
0 --> 0
1 --> 1
2 --> 10
3 --> 11
4 --> 100
5 --> 101


说明 :

0 <= n <= 105


进阶:

给出时间复杂度为 O(n*sizeof(integer)) 的解答非常容易。但你可以在线性时间 O(n) 内用一趟扫描做到吗？

```cpp
class Solution {
public:
    vector<int> countBits(int n) {
        vector<int> ret(n + 1, 0);
        for (int i = 1; i <= n; ++i) {
            ret[i] = ret[i >> 1] + (i & 1);
        }
        return ret;
    }
};
```


