Meaning: agar u se v pe koi arrow jaa rha h then pehle u ayega then v ayega
> topological sorting siff directed graph pe hota h
> topological sorting only exist in DAG (cycle nahi honi chaye)

![](https://i.imgur.com/Nkuof5H.png)

u -> v pe jab dfs call hoga tab v ko stack ke ander push kardo and uske baad u ko push kardo stack me (ye gurantee deta h while popping from stack u pehle pop hoga and then uske children which is in topological sorted order)


![](https://i.imgur.com/IYH1hqc.png)

code:
```cpp
class Solution {
   public:
    vector<bool> visited;
    stack<int> st;
    void DFS(int u, vector<int> adj[]) {
        visited[u] = true;

        // push all children into stack
        for (int &v : adj[u]) {
            if (!visited[v]) {
                DFS(v, adj);
            }
        }

        // push parent into stack
        // you have to think in terms of recursion
        // during recursion child nodes enter ho chuka h single parent ke liye
        // next time parent ko bhi enter karwana padega stack me
        st.push(u);
    }
    vector<int> topoSort(int V, vector<int> adj[]) {
        visited.resize(V, false);
        vector<int> result;

        for (int i = 0; i < V; i++) {
            if (!visited[i]) {
                DFS(i, adj);
            }
        }

        while (!st.empty()) {
            result.push_back(st.top());
            st.pop();
        }

        return result;
    }
};
```


---
#graph