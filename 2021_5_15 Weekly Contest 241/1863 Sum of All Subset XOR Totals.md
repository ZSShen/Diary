
# Problem
### LeetCode 1863. Sum of All Subset XOR Totals
https://leetcode.com/problems/sum-of-all-subset-xor-totals/

# Solution
```c++
class Solution {
public:
    int subsetXORSum(vector<int>& nums) {

        /**
         * @tag: Math, Bit Mask
         *
         * TC: O(N * (2^N)), where
         *      N is the number of elements
         *
         * SC: O(1)
         */

        int n = nums.size();
        int total = pow(2, n);
        int ans = 0;

        for (int i = 1 ; i <= total ; ++i) {
            int part = 0;

            for (int j = 0 ; j < n ; ++j) {
                if (((i >> j) & 0x1) == 0x1) {
                    part ^= nums[j];
                }
            }

            ans += part;
        }

        return ans;
    }
};
```
