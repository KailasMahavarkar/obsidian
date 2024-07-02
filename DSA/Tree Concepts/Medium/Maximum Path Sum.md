
# Leetcode 124.
## Binary Tree Maximum Path Sum

![](https://i.imgur.com/uRlsMh6.png)

```cpp

class Solution {
   public:
    int solve(TreeNode* root, int& answer) {
        if (!root) {
            return 0;
        }

        int leftSum = max(0, solve(root->left, answer));
        int rightSum = max(0, solve(root->right, answer));

        // two candidates possibilites for answer
        // 1. previous answer (answer so far) 
        // 2. sum of left path and right path + current node
        answer = max(answer, root->val + leftSum + rightSum);

        // we only send max value from left path or right to top
        return root->val + max(leftSum + rightSum);
    }

    int maxPathSum(TreeNode* root) {
        // test case:
        // [1, -1, 4, -3, 6, null, null, 5, null, null, null]
        
        //           1
        //        -1    4
        //      -3  6  x  x
        //     5 x x x

        // final answer is (6) + (-1) + (1) + (4) = 10
        int answer = INT_MIN;
        solve(root, answer);
        return answer;
    }
};
```
