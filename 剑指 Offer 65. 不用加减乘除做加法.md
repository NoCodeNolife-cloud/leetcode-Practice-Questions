写一个函数，求两个整数之和，要求在函数体内不得使用 “+”、“-”、“*”、“/” 四则运算符号。

 

示例:

输入: a = 1, b = 1
输出: 2


提示：

a, b 均可能是负数或 0
结果不会溢出 32 位整数

```cpp
class Solution {
public:
    int add(int a, int b) {
        while( b ){
            int Sumof_noJinWei= a ^ b; //a异或b为无进位求和
            //a & b后哪个位上是1，则该位相加会产生进位，而进位是左移后的结果。为保险我们强制转换为无符号整型
            int jinWei= (unsigned int)( a & b ) << 1; 

            a=Sumof_noJinWei;
            b=jinWei;//直到没有进位了，得到结果

        }
        return a;
    }
};
```

