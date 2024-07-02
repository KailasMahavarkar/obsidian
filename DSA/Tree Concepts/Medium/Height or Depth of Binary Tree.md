
how to you determine height of binary tree?
height and depth are same thing

## working
1. tum depth tak traverse karo and when recursion rolls back na that time you add 1 to its height and each node pe tum left and and right mese jo bhi max hoga usse return karo.

```cpp
class Solution {
   public:
    int findDepth(TreeNode* root) {
        if (root == NULL) {
            return 0;
        }

        int left = findDepth(root->left);
        int right = findDepth(root->right);
        return max(left, right) + 1;
    }

    int maxDepth(TreeNode* root) {
        return findDepth(root);
    }
};
```

