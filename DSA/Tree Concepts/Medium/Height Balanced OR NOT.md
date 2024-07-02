
#### Leetcode 110. Balanced Binary Tree

1) find height at each node -> left ka height find karo and right ka height find karo
2) when recursion rolls back at that moment compare if abs(h1 - h2) is more than 1 (agar true ho then its not height balanced)
![](https://i.imgur.com/mkUjzKN.png)

```cpp
class Solution {
   public:
    int findHeight(TreeNode* root) {
        if (root == NULL) {
            return 0;
        }

        int left = findHeight(root->left);
        int right = findHeight(root->right);

        return max(left, right) + 1;
    }

    bool isBalanced(TreeNode* root) {
        if (root == NULL) {
            return true;
        }

        int left = findHeight(root->left);
        int right = findHeight(root->right);

        if (
	        abs(left - right) <= 1 
	        && isBalanced(root->left) 
	        && isBalanced(root->right)
	    ) {
            return true;
        }
        return false;
    }
};

```