values[] = {1,2,3}
weight[] = {4,5,1}
capacity =  9

**Q) how to identify this is knapsack problem?**
generally in these type of problem we have limited space or capacity of storage  and we have to find best possible items with max value.
(simple example: a theif wants to steal items from a shop but he has only 1 bag with some capacity, what items shall he select to maximize his profit)

At each item we get a choice
(pick case) we can choose to pick this item
	[x] we have to reduce current capacity
	[x] increment the index and let recursion solve for smaller input case
	[x] add its own value (val[i-1] + recursion) since we picked item

(unpick / not pick) we dont pick the item
	[x] we dont reduce knapsack capacity
	[x] increment the index and let recursion solve for smaller input case

Solution 1: bruteforce using recursion 
```cpp
// METHOD 1: Basic knapsack code
class Solution {
   public:
    int knapsackHelper(int w, int wt[], int val[], int n) {
        // weight ya knapsack ki capacity hi na ho
        if (n == 0 || w == 0) {
            return 0;
        }

        // agar last weight jyada ho toh select nai kar sakte kuch bhi
        if (wt[n - 1] > w) {
            return knapsackHelper(w, wt, val, n - 1);
        } else {
            // do option honge -> pick or dont pick item
            int pickCase = val[n - 1] + knapsackHelper(w - wt[n - 1], wt, val, n - 1);
            int unpickCase = knapsackHelper(w, wt, val, n - 1);
            return max(pickCase, unpickCase);
        }
    }
    int knapSack(int W, int wt[], int val[], int n) {
        return knapsackHelper(W, wt, val, n);
    }
};
```


We can improve this algorithm, since if we draw recursive tree we can see we are solving for smaller inputs again and again instead we can cache these inputs in a memo and reuse the results whenever we need by computing any value only once.

Solution 2: recursion + memoization
```cpp
// METHOD 2: Basic knapsack code with memoization
class SolutionMemo {
   public:
    vector<vector<int>> dp;
    int knapsackHelper(int w, int wt[], int val[], int n) {
        // when capacity is zero
        // when 0 items for selection
        if (n == 0 || w == 0) {
            return 0;
        }

        // lookup in dp
        if (dp[n][w] != -1) {
            return dp[n][w];
        }

        // weight of item is more than current capacity
        if (wt[n] > w) {
            dp[n][w] = knapsackHelper(w, wt, val, n - 1);
        } else {
            int pickCase = val[n - 1] + knapsackHelper(w - wt[n - 1], wt, val, n - 1);
            int unpickCase = knapsackHelper(w, wt, val, n - 1);
            dp[n][w] = max(pickCase, unpickCase);
        }

        return dp[n][w];
    }
    int knapSack(int W, int wt[], int val[], int n) {
        dp.resize(n + 1, vector<int>(W + 1, -1));
        return knapsackHelper(W, wt, val, n);
    }
};
```

> Note: we can create dp table at beginning of the function or pass the dp table by reference i like to create table at beginning and resize it later. 


Solution 3:

```cpp
// Tabulation method
class Solution {
   public:
    int knapSack(int W, int wt[], int val[], int n) {
        vector<vector<int>> dp(n + 1, vector<int>(W + 1, -1));

        // fill 1st row and 1st column
        for (int j = 0; j < n + 1; j++) {
            dp[j][0] = 0;
        }
        for (int i = 0; i < W + 1; i++) {
            dp[0][i] = 0;
        }

        // printDP("before ", dp);
        for (int i = 1; i < n + 1; i++) {
            for (int j = 1; j < W + 1; j++) {
                if (wt[i - 1] > j) {
                    dp[i][j] = dp[i - 1][j];
                } else {
                    int pickCase = val[i - 1] + dp[i - 1][j - wt[i - 1]];
                    int unpickCase = dp[i - 1][j];
                    dp[i][j] = max(pickCase, unpickCase);
                }
            }
        }

        // printDP("after ", dp);
        return dp[n][W];
    }
};
```

tabulation: 
1) we fill the first row and first column by reference of recursion code and fill rest with -1
2) if you do understand how tabulation works this is going to be easy else you need to learn it


