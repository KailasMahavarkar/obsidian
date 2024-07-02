
![](https://i.imgur.com/q1UXyDF.png)

This question is very simple
1) you already know level order traversal of tree
2) all you need to do is when iterating over each level, just apply 1 line check (that check can be "check for 1st element" or "check for last element")
3) lets say for level 3: (6, 7 , 5, 4)
	1) just apply a check that when subiterating level if you reach at end then add the data to result


```cpp

class Solution {
   public:
    vector<int> rightSideView(TreeNode* root) {
        vector<int> answer;

        if (!root) return answer;

        queue<TreeNode*> que;
        que.push(root);

        while (!que.empty()) {
            int levelSize = que.size();

            for (int i = 0; i < levelSize; i++) {
                TreeNode* node = que.front();
                que.pop();

				// check for last element in that level
                if (i == levelSize - 1) {
                    answer.push_back(node->val);
                }

                if (node->left) {
                    que.push(node->left);
                }

                if (node->right) {
                    que.push(node->right);
                }
            }
        }

        return answer;
    }
};

```