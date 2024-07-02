Q) what is dp?
> DP is nothing but enhanced recursion

Q) 2 rules for solving recursion?
	1) identify base case (think for smallest valid input)
	2) recursion will not stop if input size is same this is the only reason we solve of array size of x and pass array size of x-1 in recursive function

Whats are common patterns in DP?
1) 0/1 knapsack
2) 0/1 knapsack (unbounded)
3) longest common subsequence
5) pallindromic longest common subsequence


####  Example of TOP down approach
```cpp
int fib(int n, vector<int> &dp){
    if (n <= 1){
        return n;
    }

    if (dp[n] != -1){
        return dp[n];
    }

    dp[n] = fib(n-1, dp) + fib(n-2, dp);
    return dp[n];
}

int main(){
    int n = 14;
    vector<int> dp(n+1, -1);

    int answer = fib(n, dp);
    printVector("dp -->", dp);

    cout << "answer --> " << answer << endl;
}

```

####  Example of Bottom up approach

```cpp

int main(){
    int n = 14;
    vector<int> dp(n+1, -1);

    dp[1] = 1;
    dp[0] = 0;

    for (int i=2; i<=n; i++){
        dp[i] = dp[i-1] + dp[i-2];
    }
    
    cout << "answer --> " << dp[n] << endl;
}
```