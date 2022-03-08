
# Problem
### LeetCode 1856. Maximum Subarray Min-Product
https://leetcode.com/problems/maximum-subarray-min-product/

# Solution
```c++
class Solution {
public:
    int maxSumMinProduct(vector<int>& nums) {

        int n = nums.size();

        stack<int> left_stk, right_stk;
        vector<int> left_bound(n, -1), right_bound(n, n);

        for (int i = 0, j = n - 1 ; i < n ; ++i, --j) {

            while (!right_stk.empty() && nums[i] < nums[right_stk.top()]) {
                int index = right_stk.top();
                right_bound[index] = i;
                right_stk.pop();
            }
            right_stk.emplace(i);

            while (!left_stk.empty() && nums[j] < nums[left_stk.top()]) {
                int index = left_stk.top();
                left_bound[index] = j;
                left_stk.pop();
            }
            left_stk.emplace(j);
        }

        vector<long long> prefix(n + 1);
        for (int i = 0 ; i < n ; ++i) {
            prefix[i + 1] = prefix[i] + nums[i];
        }

        long long ans = 0;

        for (int i = 0 ; i < n ; ++i) {
            int l = left_bound[i] + 1, r = right_bound[i] - 1;
            ans = max(ans, (prefix[r + 1] - prefix[l]) * nums[i]);
        }

        long long mod = 1e9 + 7;
        return ans % mod;
    }
};
```
