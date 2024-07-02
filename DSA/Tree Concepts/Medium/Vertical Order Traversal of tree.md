
**In the tree series I find this to be one of touf problem to solve**
difficulty: hard

![whiteboard vertical](https://i.imgur.com/Rwc30E9.jpg)

x-axis: vertical
y-axis: levels

structure of our datastructure:
```

// map<vertical, map<level, nodes[]>>
map<int, map<int, multiset<int>>>

```


```cpp
class Solution {
   public:
    vector<vector<int>> verticalTraversal(TreeNode* root) {
        vector<vector<int>> answer;

        // map<vertical, map<level, nodes[]>>
        // vertical is -X to +X | level is 0 to N

        map<int, map<int, multiset<int>>> mp;

        if (!root) {
            return answer;
        }

        queue<pair<TreeNode*, pair<int, int>>> que;
        que.push({root, {0, 0}});

        while (!que.empty()) {
            int levelSize = que.size();
            auto p = que.front();
            que.pop();

            TreeNode* node = p.first;

            int v = p.second.first;   // vertical
            int l = p.second.second;  // level

            mp[v][l].insert(node->val);

            if (node->left) {
                que.push({node->left, {v - 1, l + 1}});
            }

            if (node->right) {
                que.push({node->right, {v + 1, l + 1}});
            }
        }

        // verticalMap will be map<int, multiset<int>>
        for (auto verticalMap : mp) {
            vector<int> cols;

            // levelMap will be multiset<int>
            for (auto levelMap : verticalMap.second) {
                cols.insert(
		            cols.end(), 
		            levelMap.second.begin(),
		            levelMap.second.end()
	            );
            }

            // sort(cols.begin(), cols.end(), greater<int>());
            answer.push_back(cols);
        }

        return answer;
    }
};
```


