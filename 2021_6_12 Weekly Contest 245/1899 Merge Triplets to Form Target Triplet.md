
# Problem
### LeetCode 1899. Merge Triplets to Form Target Triplet
https://leetcode.com/problems/merge-triplets-to-form-target-triplet/

# Solution
```c++
class Solution {
public:
    bool mergeTriplets(vector<vector<int>>& tuples, vector<int>& target) {

        /**
         * @tag: Greedy
         *
         * TC: O(N), where
         *      N is number of tuples
         *
         * SC: O(1)
         */

        vector<int> res(3);

        for (const auto& tuple : tuples) {
            if (tuple[0] > target[0] ||
                tuple[1] > target[1] ||
                tuple[2] > target[2]) {
                continue;
            }

            res[0] = max(res[0], tuple[0]);
            res[1] = max(res[1], tuple[1]);
            res[2] = max(res[2], tuple[2]);
        }

        return res == target;
    }
};
```
