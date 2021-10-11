给定一个二叉搜索树的 根节点 root 和一个整数 k , 请判断该二叉搜索树中是否存在两个节点它们的值之和等于 k 。假设二叉搜索树中节点的值均唯一。

 

示例 1：

输入: root = [8,6,10,5,7,9,11], k = 12
输出: true
解释: 节点 5 和节点 7 之和等于 12
示例 2：

输入: root = [8,6,10,5,7,9,11], k = 22
输出: false
解释: 不存在两个节点值之和为 22 的节点


提示：

二叉树的节点个数的范围是  [1, 104].
-104 <= Node.val <= 104
root 为二叉搜索树
-105 <= k <= 105

```cpp
/**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     TreeNode *left;
 *     TreeNode *right;
 *     TreeNode() : val(0), left(nullptr), right(nullptr) {}
 *     TreeNode(int x) : val(x), left(nullptr), right(nullptr) {}
 *     TreeNode(int x, TreeNode *left, TreeNode *right) : val(x), left(left), right(right) {}
 * };
 */
class Solution {
public:
    bool findTarget(TreeNode* root, int k) {
        vector<int>count;
        traverse(root,count);
        for(int i=0,j=count.size()-1;i<j;){
            if(count[i]+count[j]<k){
                i++;
            }else if(count[i]+count[j]>k){
                j--;
            }else{
                return true;
            }
        }
        return false;
    }

    void traverse(TreeNode*root,vector<int>&vec){
        if(root==nullptr){
            return;
        }
        traverse(root->left,vec);
        vec.push_back(root->val);
        traverse(root->right,vec);
    }
};
```

