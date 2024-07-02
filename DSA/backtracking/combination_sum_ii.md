```cpp

class Solution {
public:
    vector<vector<int>> result;
    void combination(vector<int>& candidates, int target, vector<int> curr, int idx) {
        if(target < 0)
            return;
        if(target == 0) {
            result.push_back(curr);
            return;
        }
        
        for(int i = idx; i<candidates.size(); i++) {
            if(i > idx && candidates[i] == candidates[i-1])
                continue; //ignore duplicate elements
            curr.push_back(candidates[i]);
            combination(candidates, target-candidates[i], curr, i+1);
            curr.pop_back();
        }
    }
    vector<vector<int>> combinationSum2(vector<int>& candidates, int target) {
        vector<int> curr;
        sort(candidates.begin(), candidates.end()); //because we will ignore duplicate elements
        combination(candidates, target, curr, 0);
        return result;
    }
};

```


# Why is i > idx required?
```
i > idx && candidates[i] == candidates[i-1]

isme game simple h... i > idx ka meaning ye h ki... i toh apna current recursion ke ander h and idx ... ko observe karo (i+1) h.... so iska matlab ye hoga... i humesha left side hoga and idx humesha right side hoga

```
