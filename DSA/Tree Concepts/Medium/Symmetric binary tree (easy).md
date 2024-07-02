

![](https://i.imgur.com/W2eIJqZ.png)

simple logic:
```cpp
bool c1 = isSymmetricHelper(left->left, right->right);
bool c2 = isSymmetricHelper(left->right, right->left);
``` 
1. if left ka left matches right ka right (red line)
2. if left ka right matches right ka left (blue line)

if both conditions are true we can say its symmetric and this is checked for every single node by recursion

> can tree with no nodes be symmetric? yes

```cpp
class Solution {
   public:
    bool isSymmetricHelper(TreeNode* left, TreeNode* right) {
        if (!left || !right) {
            return left == right;
        }

        if (left->val != right->val) {
            return false;
        }

		// this is game
        bool c1 = isSymmetricHelper(left->left, right->right);
        bool c2 = isSymmetricHelper(left->right, right->left);

        return c1 && c2;
    }

    bool isSymmetric(TreeNode* root) {
	    return root == NULL || isSymmetricHelper(root->left, root->right);
    }
};

```