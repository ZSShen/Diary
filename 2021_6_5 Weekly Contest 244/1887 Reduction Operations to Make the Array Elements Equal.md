
# Problem
### LeetCode 1887. Reduction Operations to Make the Array Elements Equal
https://leetcode.com/problems/reduction-operations-to-make-the-array-elements-equal/

# Solution
```c++
class Solution {
public:
    int reductionOperations(vector<int>& nums) {

        /**
         * @tag: Sort, Ordered Map
         *
         * TC: O(NlogN), where
         *      N is the number of elements
         *
         * SC: O(1)
         */

        sort(nums.begin(), nums.end());

        int ans = 0, level = 0;
        int n = nums.size(), r = n - 1;

        for (int l = n - 1 ; l >= 0 ; --l) {
            if (nums[l] == nums[r]) {
                continue;
            }

            level += r - l;
            r = l;
            ans += level;
        }

        return ans;
    }
};
```
