给定一个字符串 s ，验证 s 是否是 回文串 ，只考虑字母和数字字符，可以忽略字母的大小写。

本题中，将空字符串定义为有效的 回文串 。

 

示例 1:

输入: s = "A man, a plan, a canal: Panama"
输出: true
解释："amanaplanacanalpanama" 是回文串
示例 2:

输入: s = "race a car"
输出: false
解释："raceacar" 不是回文串


提示：

1 <= s.length <= 2 * 105
字符串 s 由 ASCII 字符组成

```cpp
class Solution {
public:
    bool isPalindrome(string s) {
        string temp;
        for(int i=0;i<s.size();i++){
            if(isalnum(s[i])){
                temp.push_back(tolower(s[i]));
            }
        }
        for(int i=0,j=temp.size()-1;i<=j;i++,j--){
            if(temp[i]!=temp[j]){
                return false;
            }
        }
        return true;
    }
};
```


