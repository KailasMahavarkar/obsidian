
Simple Algorithm which has 3 phases
1) building indegree network
2) pushing all nodes with indegree of 0 **(remember this step you sometimes skip it)**
3) bfs traversal on network (reduce indegree while you traverse and if indegree reaches 0 then add it to the queue)

```cpp
class Solution {
   public:
    vector<int> topoSort(int V, vector<int> adj[]) {
        vector<int> result;
        unordered_map<int, int> indegree;
        queue<int> que;

        // build indegree network
        for (int i = 0; i < V; i++) {
            for (int &child : adj[i]) {
                indegree[child]++;
            }
        }

        // fill queue, with nodes having indegree 0
        for (int i = 0; i < V; i++) {
            if (indegree[i] == 0) {
                que.push(i);
            }
        }

        while (!que.empty()) {
            int curr = que.front();
            result.push_back(curr);
            que.pop();

            // visit all children of current and reduce its indegree
            // when indegree reaches 0 push it into queue
            for (int &v : adj[curr]) {
                indegree[v]--;

                if (indegree[v] == 0) {
                    que.push(v);
                }
            }
        }

        return result;
    }
};
```