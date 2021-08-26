从上到下按层打印二叉树，同一层的节点按从左到右的顺序打印，每一层打印到一行。

 

例如:
给定二叉树: [3,9,20,null,null,15,7],

```
	3
   / \
  9  20
    /  \
   15   7
```

返回其层次遍历结果：

```
[
  [3],
  [9,20],
  [15,7]
]
```


提示：

节点总数 <= 1000

```cpp
/**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     TreeNode *left;
 *     TreeNode *right;
 *     TreeNode(int x) : val(x), left(NULL), right(NULL) {}
 * };
 */
class Solution {
public:
    vector<vector<int>> levelOrder(TreeNode* root) {
        vector<vector<int>> res;
        if(root==NULL){
            return res;
        }
        vector<TreeNode*>temp;
        temp.push_back(root);
        traverse(temp,res);
        return res;
    }

    void traverse(vector<TreeNode*> root,vector<vector<int>>& result){
        if(root.size()==0){
            return;
        }
        vector<int>res;
        vector<TreeNode*>next;
        for(int i=0;i<root.size();i++){
            res.push_back(root[i]->val);
            if(root[i]->left!=NULL){
                next.push_back(root[i]->left);
            }
            if(root[i]->right!=NULL){
                next.push_back(root[i]->right);
            }
        }
        result.push_back(res);
        traverse(next,result);
    }
};
```

