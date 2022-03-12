
# Problem
### LeetCode 1870. Minimum Speed to Arrive on Time
https://leetcode.com/problems/minimum-speed-to-arrive-on-time/

# Solution
```c++
class Solution {
public:
    int minSpeedOnTime(vector<int>& dist, double hour) {

        /**
         * @tag: Binary Search
         *
         * TC: O(NlogN), where
         *      N is the number of offices
         *
         * SC: O(1)
         */

        int l = 1, r = 1e7;

        while (l + 1 < r) {
            int m = l + (r - l) / 2;
            if (canOnTime(dist, hour, m)) {
                r = m;
            } else {
                l = m;
            }
        }

        if (canOnTime(dist, hour, l)) {
            return l;
        }
        if (canOnTime(dist, hour, r)) {
            return r;
        }
        return -1;
    }

private:
    bool canOnTime(
        const vector<int>& dist, double hour, int speed) {

        double count = 0;

        int n = dist.size();
        for (int i = 0 ; i < n - 1 ; ++i) {
            count += ceil(static_cast<double>(dist[i]) / speed);
        }
        count += static_cast<double>(dist[n - 1]) / speed;

        return count <= hour;
    }
};
```
