
# Problem
### LeetCode 1886. Determine Whether Matrix Can Be Obtained By Rotation
https://leetcode.com/problems/determine-whether-matrix-can-be-obtained-by-rotation/

# Solution
```c++
class Solution {
public:
    bool findRotation(vector<vector<int>>& mat, vector<vector<int>>& target) {

        int n = mat.size();
        int count = 4;

        while (count--) {
            // Transpose
            for (int i = 0 ; i < n ; ++i) {
                for (int j = i ; j < n ; ++j) {
                    swap(mat[i][j], mat[j][i]);
                }
            }

            // Reverse
            for (int i = 0 ; i < n ; ++i) {
                reverse(mat[i].begin(), mat[i].end());
            }

            if (mat == target) {
                return true;
            }
        }

        return false;
    }
};
```
