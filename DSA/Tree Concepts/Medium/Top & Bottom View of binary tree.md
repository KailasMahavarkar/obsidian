
**PreRequisite: you must know [[Vertical Order Traversal of tree]] **

![](https://i.imgur.com/dYeciRk.png)

y-axis: represents vertical

TOP view:
so if you created vertical levels and multiple nodes exists in that level you can just maintain a map and add whenever you see a new key

Top view:
1) if it is not in hmap then add it that simple

Bottom view:
1) if key exists in map then also add it

```cpp
class Solution {
   public:
    vector<int> topView(Node* root) {
        vector<int> answer;

        if (!root) return answer;

        map<int, int> mp;
        queue<pair<Node*, int>> que;
        que.push({root, 0});

        while (!que.empty()) {
            auto p = que.front();
            que.pop();

            Node* node = p.first;
            int vertical = p.second;

            // top view: add to map only if does not exist
            // bottom view: add to map anyways
            if (mp.find(vertical) == mp.end()) {
                mp[vertical] = node->data;
            }

            if (node->left) {
                que.push({node->left, vertical - 1});
            }

            if (node->right) {
                que.push({node->right, vertical + 1});
            }
        }

        for (auto it : mp) {
            answer.push_back(it.second);
        }

        return answer;
    }
};
```

