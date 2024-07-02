
Problem statement is quite simple

![](https://i.imgur.com/Ch93uSb.jpg)

Expected: ```
```
[[3],[20,9],[15,7]]
```

Solution:
1) its a simple BFS with one variable tracking lets call it LTR(left to right)
2) LTR true indicates we are moving left to right and vice versa
3) we already have levelSize, so while filling up subvector we will perform a little math (you have to remember this math)
```
int index = LTR ? i : levelSize - i - 1;
subResult[index] = node->val;
```
there is always second option, you could just reverse the list but this will take O(n^2) time thats why its not worth it and upper method saves us 

![](https://i.imgur.com/rO3dcfY.png)


```cpp
class Solution {
   public:
    vector<vector<int>> zigzagLevelOrder(TreeNode* root) {
        vector<vector<int>> result;

        if (!root) {
            return result;
        }

        queue<TreeNode*> que;
        que.push(root);

        bool LTR = true;

        while (!que.empty()) {
            int levelSize = que.size();
            vector<int> subResult(levelSize);

            for (int i = 0; i < levelSize; i++) {
                TreeNode* node = que.front();
                que.pop();

                int index = LTR ? i : levelSize - i - 1;

                subResult[index] = node->val;

                if (node->left) {
                    que.push(node->left);
                }

                if (node->right) {
                    que.push(node->right);
                }
            }
            LTR = !LTR;
            result.push_back(subResult);
        }

        return result;
    }
};
```



