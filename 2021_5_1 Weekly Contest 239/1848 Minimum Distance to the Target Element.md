
# Problem
### LeetCode 1848. Minimum Distance to the Target Element
https://leetcode.com/problems/minimum-distance-to-the-target-element/

# Solution
```c++
class Solution {
public:
    int getMinDistance(vector<int>& nums, int target, int start) {

        /**
         * TC: O(N), where
         *      N is the size of the vector
         *
         * SC: O(1)
         */

        int ans = INT_MAX;
        int n = nums.size();

        for (int i = 0 ; i < n ; ++i) {
            if (nums[i] == target) {
                ans = min(ans, abs(i - start));
            }
        }

        return ans;
    }
};
```
