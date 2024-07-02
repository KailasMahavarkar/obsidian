
![](https://i.imgur.com/ahBvWyM.png)

agar node visited h then usko check karo.... if it is in recursion, agar vo current recursion me bhi h then pakka cycle hoga

```cpp
class Solution {
   public:
    vector<bool> visited;
    vector<bool> inRecursion;
    bool isCycleDFS(int curr, vector<int> adj[]) {
        // mark visited
        visited[curr] = true;
        inRecursion[curr] = true;

        for (int &child : adj[curr]) {
            // if not visited then we check for cycle in DFS
            if (visited[child] == false) {
                if (isCycleDFS(child, adj)) {
                    return true;
                }
            }

            // visited and it is in current recursion
            if (inRecursion[child]) {
                return true;
            }
        }

        inRecursion[curr] = false;
        return false;
    }

    bool isCyclic(int V, vector<int> adj[]) {
        visited.resize(V, false);
        inRecursion.resize(V, false);

        // we are assuming graphs are component based
        for (int i = 0; i < V; i++) {
            // when node is not visited
            if (!visited[i]) {
                if (isCycleDFS(i, adj)) {
                    return true;
                }
            }
        }
        return false;
    }
};
```