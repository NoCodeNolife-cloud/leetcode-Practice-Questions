给定一个非空的正整数数组 nums ，请判断能否将这些数字分成元素和相等的两部分。

 

示例 1：

输入：nums = [1,5,11,5]
输出：true
解释：nums 可以分割成 [1, 5, 5] 和 [11] 。
示例 2：

输入：nums = [1,2,3,5]
输出：false
解释：nums 不可以分为和相等的两部分


提示：

1 <= nums.length <= 200
1 <= nums[i] <= 100

```cpp
class Solution {
public:
    bool canPartition(vector<int>& nums) {
        int len = nums.size();
        if(len==1) return false;
        int sum = 0;
        for(int i : nums) sum += i;
        if(sum&1) return false;
        int tar = sum >> 1 ;
        bool dp[tar+1];
        memset(dp,0,sizeof(dp));//初始化
        dp[0] = true;
        for(int i =0 ; i< len ; ++i){
            for(int j=tar ; j>=nums[i] ; --j){
                if(dp[j-nums[i]]==true) dp[j]=true;
            }
        }
        return dp[tar];
    }
};
```

