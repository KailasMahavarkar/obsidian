
![](https://i.imgur.com/dxq2uKj.png)

```cpp
// pseudo logic code
DFS(adj, u, visited, parent){
	visited[u] = true
	for (int &v: adj[u]){
		if (v == parent) continue;
		if (visited[v] == True){
			// pakka cycle h
			return True
		}

		if (DFS(adj, v, visited, u)){
			// childrens ke dfs call me cycle detect ho gyi
			return True
		}
	}
}

return False
```

code:
```cpp

class Solution {
  public:
    vector<bool> visited;
    bool isCycleDFS(vector<int> adj[], int current, int parent){
        // mark node visited
        visited[current] = true;
        
        // from that current node visit next all its neighbours
        for (int &v: adj[current]){
            
            // skip parent position since we came from that point
            // if we go back it will be considered as cycle even though its not
            if (v == parent){
                continue;
            }
            
            if (visited[v]){
                // we found cycle since node is visited twice
                return true;
            }

            if (isCycleDFS(adj, v, current)){
                return true;
            }
        }
        
        return false;
    }
    bool isCycle(int V, vector<int> adj[]){
        visited.resize(V, false);
        
        // we are assuming graphs are component based 
        for(int i=0; i<V; i++){
            // when node is not visited
            if (!visited[i]){
                if (isCycleDFS(adj, i, -1)){
                    return true;
                }
            }
        }
        return false; 
    }
};
```


----
#graph 