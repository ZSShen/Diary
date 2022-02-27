
# Problem
### LeetCode 1817. Finding the Users Active Minutes
https://leetcode.com/problems/finding-the-users-active-minutes/

# Solution
```c++
class Solution {
public:
    vector<int> findingUsersActiveMinutes(vector<vector<int>>& logs, int k) {

        /**
         * @tag: Hash Table
         *
         * TC: O(N), where
         *      N is the number of log lines
         *
         * SC: O(N)
         */

        unordered_map<int, unordered_set<int>> map;
        for (const auto& log : logs) {
            map[log[0]].emplace(log[1]);
        }

        vector<int> ans(k);
        for (const auto& kv : map) {
            ++ans[kv.second.size() - 1];
        }
        return ans;
    }
};
```
