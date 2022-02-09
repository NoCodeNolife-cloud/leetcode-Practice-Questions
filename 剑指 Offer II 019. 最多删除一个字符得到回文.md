给定一个非空字符串 `s`，请判断如果 **最多** 从字符串中删除一个字符能否得到一个回文字符串。示例 1:

输入: s = "aba"
输出: true
示例 2:

输入: s = "abca"
输出: true
解释: 可以删除 "c" 字符 或者 "b" 字符
示例 3:

输入: s = "abc"
输出: false


提示:

1 <= s.length <= 105
s 由小写英文字母组成

```c++
class Solution {
public:
    bool validPalindrome(string s) {
        int left=0,right=s.size()-1;
        while(left<=right&&s[left]==s[right]){
            left++;
            right--;
        }
        if(left<=right){
            int tleft=left+1,tright=right;
            while(tleft<=tright&&s[tleft]==s[tright]){
                tleft++;
                tright--;
            }
            if(tleft>tright){
                return true;
            }
            tleft=left;
            tright=right-1;
            while(tleft<=tright&&s[tleft]==s[tright]){
                tleft++;
                tright--;
            }
            if(tleft>tright){
                return true;
            }
        }else{
            return true;
        }
        return false;
    }
};
```

```java
class Solution {
    public boolean validPalindrome(String s) {
        int left=0,right=s.length()-1;
        while(left<=right&&s.charAt(left)==s.charAt(right)){
            left++;
            right--;
        }
        if(left<=right){
            int tleft=left+1,tright=right;
            while(tleft<=tright&&s.charAt(tleft)==s.charAt(tright)){
                tleft++;
                tright--;
            }
            if(tleft>tright){
                return true;
            }
            tleft=left;
            tright=right-1;
            while(tleft<=tright&&s.charAt(tleft)==s.charAt(tright)){
                tleft++;
                tright--;
            }
            if(tleft>tright){
                return true;
            }
        }else{
            return true;
        }
        return false;
    }
}
```

