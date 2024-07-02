
![](https://i.imgur.com/lyt4zxE.png)

Diameter of binary tree
1. longest path between any two nodes
2. it does not need to be passing from root


```cpp
class Solution {
   public:
    int findDiameter(TreeNode* root, int& answer) {
        if (!root) {
            return 0;
        }

        int left = findDiameter(root->left, answer);
        int right = findDiameter(root->right, answer);

		// this is is different rest code is height of tree
		// we are storing maximum in global state
        answer = max(answer, left + right);
        return max(left, right) + 1;
    }
    int diameterOfBinaryTree(TreeNode* root) {
        int answer = 0;
        findDiameter(root, answer);
        return answer;
    }
};

```

> note: variable answer is passed by reference in this case