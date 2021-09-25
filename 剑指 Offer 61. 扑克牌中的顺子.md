从若干副扑克牌中随机抽 5 张牌，判断是不是一个顺子，即这5张牌是不是连续的。2～10为数字本身，A为1，J为11，Q为12，K为13，而大、小王为 0 ，可以看成任意数字。A 不能视为 14。



示例 1:

输入: [1,2,3,4,5]
输出: True


示例 2:

输入: [0,0,1,2,5]
输出: True


限制：

数组长度为 5 

数组的数取值为 [0, 13] .

```cpp
class Solution {
public:
    bool isStraight(vector<int>& nums) {
        sort(nums.begin(), nums.end());
        int king = 0;
        for (int i = 0; i < nums.size() -1; i ++) {
            // 统计大小王个数
            if (nums[i] == 0) {
                king ++;
                continue;
            }
            // 若当前数字与之后数字相等（不符合顺子要求）返回false
            if (nums[i] == nums[i + 1])
                return false;
            // 若当前数字与之后数字是否只相差 1（符合顺子要求）直接判断下一张牌
            if (nums[i + 1] == nums[i] + 1)
                continue;
            // 若当前数字与之后数字相差大于 1，则不够的中间牌可以用大小王去替，
            // 若大小王的数量不够则返回false，够则检查下一张排
            if (nums[i + 1] > nums[i] + 1) {
                king -= nums[i + 1] - nums[i] - 1;
                if (king < 0 )
                    return false;
            }
        }
        return true;
    }
};
```

