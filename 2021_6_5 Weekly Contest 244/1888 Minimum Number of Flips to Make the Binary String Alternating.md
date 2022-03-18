
# Problem
### LeetCode 1888. Minimum Number of Flips to Make the Binary String Alternating
https://leetcode.com/problems/minimum-number-of-flips-to-make-the-binary-string-alternating/

# Solution
```c++
class Solution {
public:
    int minFlips(string s) {

        /**
         * @tag: Greedy, Sliding Window
         *
         * TC: O(N), where
         *      N is the string length
         *
         * SC: O(1)
         */

        int n = s.length();
        int nn = n << 1;

        int count_0 = 0, count_1 = 0;
        int ans = INT_MAX;

        for (int i = 0 ; i < nn ; ++i) {
            if ((i & 0x1) == 0x0) {
                count_0 += s[i % n] != '0';
                count_1 += s[i % n] != '1';
            } else {
                count_0 += s[i % n] != '1';
                count_1 += s[i % n] != '0';
            }

            if (i >= n - 1) {
                ans = min(ans, min(count_0, count_1));

                int j = i - n + 1;
                if ((j & 0x1) == 0x0) {
                    count_0 -= s[j] != '0';
                    count_1 -= s[j] != '1';
                } else {
                    count_0 -= s[j] != '1';
                    count_1 -= s[j] != '0';
                }
            }
        }

        return ans;
    }
};
```
