
```cpp
class Solution {
public:
    vector<vector<int>> directions = {{-1, 0}, {0, -1}, {1, 0}, {0, 1}};
    int m, n;
    bool find(vector<vector<char>> &board, string &word, int i, int j, int idx){
        // base case for success
        if (idx >= word.length()){
            return true;
        }

        // base case for failure
        if (i < 0 || i >= m || j < 0 || j >= n || board[i][j] != word[idx]){
            return false;
        }

        // backtracking begins
        char temp = board[i][j];
        board[i][j] = '#';
        for (auto &dir: directions){ 
            if (find(board, word, i+dir[0], j+dir[1], idx+1)){
                return true;
            }
        }
        board[i][j] = temp;
        // backtracking ends

        return false;
    }
    bool exist(vector<vector<char>>& board, string word) {
        m = board.size();
        n = board[0].size();

        for (int i=0; i<m; i++){
            for (int j=0; j<n;j++){
                if (board[i][j] == word[0]){
                    if (find(board, word, i, j, 0)){
                        return true;
                    }
                }
            }
        }

        return false;
    }
};
```


## Intuition:

In the very beginning, we check if grid's `ith` position matches with the word's `ith` position in the board, if so return from that point, otherwise our current character is  good and we will make recursive calls to neighbors cells hoping recursion will find solution.

> Note: In each recursive call we check `ith` word and then make recursive calls to neighbor to match `(i+1)th` and so on till we find `(i+k)th` correct word, where k is size of word matches, remember that instance where it fails we return from that point.