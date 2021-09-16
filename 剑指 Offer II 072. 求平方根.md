给定一个非负整数 x ，计算并返回 x 的平方根，即实现 int sqrt(int x) 函数。

正数的平方根有两个，只输出其中的正数平方根。

如果平方根不是整数，输出只保留整数的部分，小数部分将被舍去。

 

示例 1:

输入: x = 4
输出: 2
示例 2:

输入: x = 8
输出: 2
解释: 8 的平方根是 2.82842...，由于小数部分将被舍去，所以返回 2


提示:

0 <= x <= 231 - 1

```cpp
class Solution {
public:
    int mySqrt(int x) {
        long long res=0;
        while(res*res<=x){
            if((res+1000)*(res+1000)<=x){
                res+=1000;
            }else if((res+100)*(res+100)<=x){
                res+=100;
            }else if((res+10)*(res+10)<=x){
                res+=10;
            }else{
                res++;
            }
        }
        return res-1;
    }
};
```

