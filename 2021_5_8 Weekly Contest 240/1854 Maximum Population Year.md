
# Problem
### LeetCode 1854. Maximum Population Year
https://leetcode.com/problems/maximum-population-year/

# Solution
```c++
class Solution {
public:
    int maximumPopulation(vector<vector<int>>& logs) {

        /**
         * @tag: Sweep Line
         *
         * TC: O(N), where
         *      N is the total number of years
         *
         * SC: O(N)
         */

        vector<int> pops(MAX);

        for (const auto& log : logs) {
            ++pops[log[0] - BASE];
            --pops[log[1] - BASE];
        }

        int count = 0, max_count = INT_MIN, ans = -1;
        for (int i = 0 ; i < MAX ; ++i) {
            count += pops[i];
            if (count > max_count) {
                max_count = count;
                ans = i;
            }
        }

        return ans + BASE;
    }

private:
    static const int MAX = 101;
    static const int BASE = 1950;
};
```
