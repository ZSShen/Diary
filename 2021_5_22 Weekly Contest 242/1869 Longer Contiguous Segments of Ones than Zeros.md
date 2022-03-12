
# Problem
### LeetCode 1869. Longer Contiguous Segments of Ones than Zeros
https://leetcode.com/problems/longer-contiguous-segments-of-ones-than-zeros/

# Solution
```c++
class Solution {
public:
    bool checkZeroOnes(string s) {

        /**
         * @tag: Two Pointers
         *
         *
         * TC: O(N), where
         *      N is the string length
         *
         * SC: O(1)
         */

        int n = s.length();
        int max_0 = 0, max_1 = 0;

        int l = 0;
        for (int r = 0 ; r <= n ; ++r) {
            if (r < n && s[r] == s[l]) {
                continue;
            }

            if (s[l] == '0') {
                max_0 = max(max_0, r - l);
            } else {
                max_1 = max(max_1, r - l);
            }

            l = r;
        }

        return max_1 > max_0;
    }
};
```
