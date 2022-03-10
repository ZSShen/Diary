
# Problem
### LeetCode 1818. Minimum Absolute Sum Difference
https://leetcode.com/problems/minimum-absolute-sum-difference/

# Solution
```c++
class Solution {
public:
    int minAbsoluteSumDiff(vector<int>& nums1, vector<int>& nums2) {

        /**
         * @tag: Binary Search, Sort, Ordered Set
         *
         * TC: O(NlogN), where
         *      N is the size of the input vectors
         *
         * SC: O(N)
         */

        long mod = 1e9 + 7;
        long sum = 0;

        set<int> set;
        int n = nums1.size();
        for (int i = 0 ; i < n ; ++i) {
            sum += abs(nums1[i] - nums2[i]);
            set.emplace(nums1[i]);
        }

        long ans = sum;
        for (int i = 0 ; i < n ; ++i) {
            auto it = set.upper_bound(nums2[i]);

            if (it != set.end()) {
                long new_sum = sum - abs(nums1[i] - nums2[i]);
                new_sum += abs(*it - nums2[i]);
                ans = min(ans, new_sum);
            }
            if (it != set.begin()) {
                --it;
                long new_sum = sum - abs(nums1[i] - nums2[i]);
                new_sum += abs(*it - nums2[i]);
                ans = min(ans, new_sum);
            }
        }

        return ans % mod;
    }
};
```
