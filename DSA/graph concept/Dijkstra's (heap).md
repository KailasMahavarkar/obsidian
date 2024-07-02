
![](https://i.imgur.com/Nn3CWQQ.png)

> Next create result array to store all distance by default all values are INT_MAX

```cpp
{
	2: {0, 6}, {1, 3},
	1: {2, 3}, {0, 1},
	0: {1, 1}, {2, 6}
}
// OUR source is 2 <- read it
// starting from 2 we can visit 0 with cost of 6
// starting from 2 we can visit 1 with cost of 3
// adj[parent] = [{node, cost}, {node, cost}]

// storing in the min-heap <- this is game
// pair<int, int> <- {cost, node}

```

```cpp

class Solution
{
	public:
	//Function to find the shortest distance of all the vertices
    //from the source vertex S.
    vector <int> dijkstra(int V, vector<vector<int>> adj[], int S)
    {
        // shape of adj is {node, weight}
        vector<int> result(V, INT_MAX);

        // 1. building heap
        // shape of pq {weight, node}
        priority_queue<pair<int, int>, vector<pair<int, int>>, greater<pair<int, int>>> pq;
        
        // 2. initalize the heap with source -> source as 0
        pq.push({0, S});
        
        // 3. make sure result[S] is 0 -> it takes 0 time to reach source
        result[S] = 0;

        
        while(!pq.empty()){
            int weight = pq.top().first;
            int node = pq.top().second;
            pq.pop();
            
            for(auto &child: adj[node]){
                int adjNode = child[0]; // shape of adj[x][0] belongs to node
                int d = child[1]; // shape of adj[x][1] belongs to distance
                
                if (d+weight < result[adjNode]){
                    result[adjNode] = d+weight;
                    pq.push({d+weight, adjNode});
                }
                
            }
        }
        
        return result;
    }
};

```


---
#graph #dsa