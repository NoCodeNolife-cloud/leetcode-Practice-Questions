请实现一个函数，用来判断一棵二叉树是不是对称的。如果一棵二叉树和它的镜像一样，那么它是对称的。

例如，二叉树 [1,2,2,3,4,4,3] 是对称的。

```
	1
   / \
  2   2
 / \ / \
3  4 4  3
```

但是下面这个 [1,2,2,null,3,null,3] 则不是镜像对称的:

```
	1
   / \
  2   2
   \   \
   3    3
```



示例 1：

输入：root = [1,2,2,3,4,4,3]
输出：true
示例 2：

输入：root = [1,2,2,null,3,null,3]
输出：false


限制：

0 <= 节点个数 <= 1000

```cpp
class Solution {
public:
    bool isSymmetric(TreeNode* root) {
        return isSymmetric(root, root);
    }

    // 重载
    bool isSymmetric(TreeNode* pRoot1, TreeNode* pRoot2)  {
        // 对称位置均为空, 肯定对称
        if (pRoot1 == nullptr && pRoot2 == nullptr) return true;
        // 对称位置有一个不为空, 肯定不对称
        if (pRoot1 == nullptr || pRoot2 == nullptr) return false;
        // 对称位置的值不相等,返回false
        if (pRoot1->val != pRoot2->val) return false;
        // 递归
        return isSymmetric(pRoot1->left, pRoot2->right) && isSymmetric(pRoot1->right, pRoot2->left);
    }
};
```

