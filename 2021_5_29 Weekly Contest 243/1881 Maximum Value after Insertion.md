
# Problem
### LeetCode 1881. Maximum Value after Insertion
https://leetcode.com/problems/maximum-value-after-insertion/

# Solution
```c++
class Solution {
public:
    string maxValue(string s, int x) {

        /**
         * @tag: Greedy
         *
         * TC: O(N), where
         *      N is the string length
         *
         * SC: O(1)
         */

        bool negative = s[0] == '-';

        int n = s.length();
        int i = negative ? 1 : 0;
        string res = negative ? "-" : "";

        while (i < n) {
            if (negative ? s[i] - '0' > x : s[i] - '0' < x) {
                break;
            }
            res.push_back(s[i++]);
        }

        res.push_back(x + '0');
        while (i < n) {
            res.push_back(s[i++]);
        }

        return res;
    }
};
```
