![](https://i.imgur.com/3iQVl5O.png)

```python

# subsets (pure recursion -> base case hits at end of recursion stack)

from typing import List

def solve(nums: List[int], temp: List[int], idx: int, answer: List[List[int]]):
    if idx == len(nums):
        answer.append(temp[:])
        return

    # exclude
    solve(nums, temp, idx + 1, answer)

    # include
    temp.append(nums[idx])
    solve(nums, temp, idx + 1, answer)
    temp.pop()

def subsets(nums: List[int]) -> List[List[int]]:
    nums.sort()
    answer = []
    solve(nums, [], 0, answer)
    return answer

```

In this example, the base case is executed always at end, which means we are not pruning any branches like we expect in backtracking problems which means we are performing pure-recursion (in conclusion `subsets-1` is a bad example to understand backtracking concepts)


```python

# subsets (forward iterative -> recursion)

from typing import List

def solve(nums: List[int], temp: List[int], idx: int, answer: List[List[int]]):
    answer.append(temp[:])

    for i in range(idx, len(nums)):
        temp.append(nums[i])
        solve(nums, temp, i + 1, answer)
        temp.pop()
    

def subsetsIterative(nums: List[int]) -> List[List[int]]:
    nums.sort()
    answer = []
    solve(nums, [], 0, answer)
    return answer

```


```

recursion call will be executed like:
0
	-> 1, 2
		-> 2
1
	-> 2
2

so its like DFS (call for 0 will be executed) then call for 1 is executed

Conclusion:
forward recursion in backtracking acts like DFS
Pure Recursion(15 recursive calls)
Iterative Recursion (8 recursive calls)

```


There are basically two ways to call recursion
1. exclude include case
2. iterative approach

