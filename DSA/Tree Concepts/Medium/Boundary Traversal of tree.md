
lets remember basics to solve this question
1) any node will be considered leaf if his left child is not present and his child is not present 
2) to print boundary you have to traverse in chunks 
	1) print left nodes
	2) print leaf nodes
	3) print right nodes

```cpp
// when you are printing boundary for left then you have to check // left first and same with right
if (curr->left) {
	curr = curr->left;
} else {
	curr = curr->right;
}
```


Final Code:

```cpp
class Solution {
   public:
    Node* rootNode;

    bool isLeaf(Node* root) {
        return !root->left && !root->right;
    }

    void addLeftBoundary(Node* root, vector<int>& res) {
        Node* curr = root->left;

        while (curr) {
            if (!isLeaf(curr)) {
                res.push_back(curr->data);
            }

            if (curr->left) {
                curr = curr->left;
            } else {
                curr = curr->right;
            }
        }
    }

    void addRightBoundary(Node* root, vector<int>& res) {
        Node* curr = root->right;
        vector<int> temp;

        while (curr) {
            if (!isLeaf(curr)) {
                temp.push_back(curr->data);
            }

            if (curr->right) {
                curr = curr->right;
            } else {
                curr = curr->left;
            }
        }

        for (int i = temp.size() - 1; i >= 0; --i) {
            res.push_back(temp[i]);
        }
    }

    void addLeaves(Node* root, vector<int>& res) {
        if (isLeaf(root)) {
            res.push_back(root->data);
            return;
        }

        if (root->left) {
            addLeaves(root->left, res);
        }

        if (root->right) {
            addLeaves(root->right, res);
        }
    }

    vector<int> boundary(Node* root) {
        vector<int> answer;

        if (!root) {
            return answer;
        }

        if (!isLeaf(root)) {
            answer.push_back(root->data);
        }

        addLeftBoundary(root, answer);
        addLeaves(root, answer);
        addRightBoundary(root, answer);

        return answer;
    };
};
```


if you still dont understand, you have to watch striver video on this topic 
(9 mins): https://www.youtube.com/watch?v=0ca1nvR0be4