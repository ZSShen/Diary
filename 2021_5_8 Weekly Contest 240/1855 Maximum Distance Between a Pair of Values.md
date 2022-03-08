
# Problem
### LeetCode 1855. Maximum Distance Between a Pair of Values
https://leetcode.com/problems/maximum-distance-between-a-pair-of-values/

# Solution
```c++
class Solution {
public:
    int maxDistance(vector<int>& nums1, vector<int>& nums2) {

        /**
         * @tag: Two Pointers, Binary Search
         *
         * TC: O(N), where
         *      N is the number of elements
         *
         * SC: O(1)
         */

        int ans = 0;
        int n1 = nums1.size(), n2 = nums2.size();
        int i = 0, j = 0;

        while (i < n1 && j < n2) {
            if (nums1[i] > nums2[j]) {
                ++i;
            } else {
                ans = max(ans, j - i);
                ++j;
            }
        }

        return ans;
    }
};
```
