
# Problem
### LeetCode 1833. Maximum Ice Cream Bars
https://leetcode.com/contest/weekly-contest-237/problems/maximum-ice-cream-bars/

# Solution
```c++
class Solution {
public:
    int maxIceCream(vector<int>& costs, int coins) {

        /**
         * @tag: Sort
         *
         * TC: O(NlogN), where
         *      N is the number of costs
         *
         * SC: O(1)
         */

        sort(costs.begin(), costs.end());

        int ans = 0;

        for (int cost : costs) {
            coins -= cost;
            if (coins < 0) {
                break;
            }
            ++ans;
        }

        return ans;
    }
};
```
