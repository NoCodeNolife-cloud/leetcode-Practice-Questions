给定一个链表的 头节点 head ，请判断其是否为回文链表。

如果一个链表是回文，那么链表节点序列从前往后看和从后往前看是相同的。

 

示例 1：

![img](剑指 Offer II 027. 回文链表.assets/1626421737-LjXceN-image.png)

输入: head = [1,2,3,3,2,1]
输出: true
示例 2：

![img](剑指 Offer II 027. 回文链表.assets/1626422231-wgvnWh-image.png)

输入: head = [1,2]
输出: false


提示：

链表 L 的长度范围为 [1, 105]
0 <= node.val <= 9


进阶：能否用 O(n) 时间复杂度和 O(1) 空间复杂度解决此题？

```c++
/**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     ListNode *next;
 *     ListNode() : val(0), next(nullptr) {}
 *     ListNode(int x) : val(x), next(nullptr) {}
 *     ListNode(int x, ListNode *next) : val(x), next(next) {}
 * };
 */
class Solution {
public:
    bool isPalindrome(ListNode* head) {
        vector<int>res;
        while(head!=NULL){
            res.push_back(head->val);
            head=head->next;
        }
        for(int i=0,j=res.size()-1;i<=j;i++,j--){
            if(res[i]!=res[j]){
                return false;
            }
        }
        return true;
    }
};
```

```java
class Solution {
    public boolean isPalindrome(ListNode head) {
        List<Integer> vals = new ArrayList<Integer>();

        // 将链表的值复制到数组中
        ListNode currentNode = head;
        while (currentNode != null) {
            vals.add(currentNode.val);
            currentNode = currentNode.next;
        }

        // 使用双指针判断是否回文
        int front = 0;
        int back = vals.size() - 1;
        while (front < back) {
            if (!vals.get(front).equals(vals.get(back))) {
                return false;
            }
            front++;
            back--;
        }
        return true;
    }
}
```

