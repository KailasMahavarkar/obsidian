```cpp
class Solution {
public:
    vector<vector<int>> answer;
    void solve(int index, int target, vector<int> &temp, vector<int> &candidates){
        // maximum recursion depth candiates size ke barabar ho sakta h
        // meaning ... agar tum recursion tree bana dete hona tab observe karna
        // pick ke case me toh vo unlimited number of times chalega... isko limit karna padega
        // and yahi se recursion rollback bhi karenge hum
        if (index == candidates.size()){
            if (target == 0){
                answer.push_back(temp);
            }
            return;
        }


        // pick case
        if (candidates[index] <= target){
            temp.push_back(candidates[index]);
            solve(index, target - candidates[index], temp, candidates);
            temp.pop_back();
        }

        // unpick case
        solve(index + 1, target, temp, candidates);

    }
    vector<vector<int>> combinationSum(vector<int>& candidates, int target) {
        vector<int> ds; 
        solve(0, target, ds, candidates);
        return answer;
    }
};


```