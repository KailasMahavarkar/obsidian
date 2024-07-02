
![](https://i.imgur.com/guXJiB9.jpg)

Tree can only be same 
1) when both trees nodes are NULL
2) when both values of nodes are matching

```cpp
class Solution {
public:
    // A tree can only be same 
    // 1) when both trees nodes are NULL
    // 2) when both values of nodes are matching
    // below code demonstrates opposite condition to break recursion when not same
    bool isSameTree(TreeNode* p, TreeNode* q) {
        // both nodes are pointing to null
        // meaning: both are null so they are same thus we return true
        if (p == NULL && q == NULL){
            return true;
        }
        
        // one of node is pointing to null
        if (p == NULL || q == NULL){
            return false;
        }
        
        // when values does not match
        if (p->val != q->val){
            return false;
        }

        return isSameTree(p->left, q->left) && isSameTree(p->right, q->right);
    }
};
```




