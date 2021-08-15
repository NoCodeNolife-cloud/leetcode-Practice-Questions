给定两个 01 字符串 a 和 b ，请计算它们的和，并以二进制字符串的形式输出。

输入为 非空 字符串且只包含数字 1 和 0。

 

示例 1:

输入: a = "11", b = "10"
输出: "101"
示例 2:

输入: a = "1010", b = "1011"
输出: "10101"


提示：

每个字符串仅由字符 '0' 或 '1' 组成。
1 <= a.length, b.length <= 10^4
字符串如果不是 "0" ，就都不含前导零。

```cpp
class Solution {
public:
    string addBinary(string a, string b) {
        string res;
        reverse(a.begin(),a.end());
        reverse(b.begin(),b.end());
        int len=(a.size()>b.size())?a.size():b.size();
        int carray=0;
        for(int i=0;i<len;i++){
            int temp1,temp2;
            if(i<a.size()){
                temp1=a[i]-'0';
            }else{
                temp1=0;
            }
            if(i<b.size()){
                temp2=b[i]-'0';
            }else{
                temp2=0;
            }
            char tp=((temp1+temp2+carray)%2==0)?'0':'1';
            carray=(temp1+temp2+carray>=2)?1:0;
            res.insert(res.begin(),tp);
        }
        if(carray==1){
            res.insert(res.begin(),'1');
        }
        return res;
    }
};
```

