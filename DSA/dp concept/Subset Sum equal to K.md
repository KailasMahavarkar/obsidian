
```cpp
#include <bits/stdc++.h>
using namespace std;

void printDP(string msg, vector<vector<bool>>& dp) {
    cout << msg << " " << endl;
    for (int i = 0; i < dp.size(); i++) {
        for (int j = 0; j < dp[0].size(); j++) {
            cout << dp[i][j] << " ";
        }
        cout << endl;
    }
    cout << endl;
}

recursion + dp
class Solution {
   public:
    int target;
    vector<vector<bool>> dp;
    bool isSubsetSumHelper(vector<int> arr, int sum, int n) {
        if (sum == 0) {
            return true;
        }
        if (n == 0) {
            return false;
        }

        if (dp[n - 1][sum] != 0) {
            return dp[n - 1][sum];
        }

        // if last element is more than target ignore it and move to next
        if (arr[n - 1] > sum) {
            dp[n][sum] = isSubsetSumHelper(arr, sum, n - 1);
        } else {
            bool pickCase = isSubsetSumHelper(arr, sum - arr[n - 1], n - 1);
            bool unpickCase = isSubsetSumHelper(arr, sum, n - 1);
            dp[n][sum] = pickCase || unpickCase;
        }

        return dp[n][sum];
    }
    bool isSubsetSum(vector<int> arr, int sum) {
        target = sum;
        dp.resize(arr.size() + 1, vector<bool>(sum + 1, false));

        // printDP("before", dp);
        bool ans = isSubsetSumHelper(arr, sum, arr.size());
        // printDP("after", dp);
        return ans;
    }
};

```