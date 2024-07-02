
Maximum Width of binary tree: 
maximum width of binary tree is maximum width between any two nodes at any given level (yes correct **level**)

Example  1:
you have tree which looks like, so what it the maximum width of the tree?
![](https://i.imgur.com/RmnpcJg.png)



> answer: 8 

----

Example 2: 
what about this one?
![](https://i.imgur.com/YQlub2E.png)



> answer: 7
> simple we dont consider null nodes if it is on either end



Solution
1) so if we knew index of each tree node, we could just compare index of starting node and ending node of that level and just add 1 to it

level 1 
s = 1
e = 1
e - s + 1 = 1

level 2:
s = 2
e = 3
e - s + 1 = (3 - 2) + 1 = 2

level 3:
s = 4
e = 7
e - s + 1 = (7 - 4) + 1 = 4

level 4:
s = 8
e = 15
e - s + 1 = (15 - 8 + 1) = (7 + 1) = 8


>indexing formula (this you have to remember)
>while doing BFS apply below logic while saving node
>1) when you move left you do "2 * idx + 1"
>2) when you move right you do "2 * idx + 2"

```
long start = que.front().second;
long end = que.back().second;
answer = max(answer, end - start + 1);

Remember: 
end - start + 1... max possible level
(15 - 8 + 1) = (7 + 1) = 8 <--- this is answer
```


![](https://i.imgur.com/sPC2AmH.png)

Code:
```cpp
class Solution {
   public:
    int widthOfBinaryTree(TreeNode* root) {
        queue<pair<TreeNode*, int>> que;
        que.push({root, 0});
        long answer = 0;

        while (!que.empty()) {
            int levelSize = que.size();
            long start = que.front().second;
            long end = que.back().second;
            answer = max(answer, end - start + 1);

            for (int i = 0; i < levelSize; i++) {
                auto x = que.front();
                que.pop();

                TreeNode* node = x.first;
                long idx = x.second;

                if (node->left) {
                    que.push({node->left, 2 * idx + 1});
                }

                if (node->right) {
                    que.push({node->right, 2 * idx + 2});
                }
            }
        }

        return answer;
    }
};
```