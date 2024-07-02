Given an array of `n` integers `nums`, a **132 pattern** is a subsequence of three integers `nums[i]`, `nums[j]` and `nums[k]` such that `i < j < k` and `nums[i] < nums[k] < nums[j]`

Return `true` _if there is a **132 pattern** in_ `nums`_, otherwise, return_ `false`

---
> Core Intuition with example dry run

lets take example `132`
We iterate from `last -> first`

`Iteration 1:`
we push last element to stack `[2]`

`Iteration 2:`
our curr is `3`... and our stack has `2` on top... so we push greater element and mark whatever is on top of stack as our `num3`

> Look carefully, with this we have solved  2 things ... we got our  `3rd element` and `2nd element` now all we need in next iteration is to find element which is less than num3

`Iteration 3:`
our curr is `1` and our nums3 = `2` ... if curr < nums3 ... we return true






