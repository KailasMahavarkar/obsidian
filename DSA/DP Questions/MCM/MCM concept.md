
```
f(i, j) = A + B + C

A -> f(i, k)
B -> f(k+1, j)
C -> (number of OPERATIONS to required to mutliply matrices of dimension (arr[i-1], arr[k]) and (arr[k], arr[j])

Question is about number of operations... not the values of them, so for the values we can say:
(AxB) x (BxC) -> operations are always AxBxC... where B has to match in both matrices
```


```cpp

class SolutionMemo {
   public:
    int global_min = INT_MAX;
    int dp[101][101];
    int solve(int arr[], int i, int j) {
        if (i >= j) {
            return dp[i][j] = 0;
        }

        if (dp[i][j] != -1) {
            return dp[i][j];
        }

        int local_min = INT_MAX;

        for (int k = i; k < j; k++) {
            int leftHalf = solve(arr, i, k);
            int rightHalf = solve(arr, k + 1, j);
            int current_cost = arr[i - 1] * arr[k] * arr[j];
            local_min = min(leftHalf + rightHalf + current_cost, local_min);
        }

        dp[i][j] = local_min;
        return local_min;
    }

    int matrixMultiplication(int N, int arr[]) {
        memset(dp, -1, sizeof(dp));
        return solve(arr, 1, N - 1);
    }
};




```