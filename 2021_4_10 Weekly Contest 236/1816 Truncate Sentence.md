
# Problem
### LeetCode 1816. Truncate Sentence
https://leetcode.com/problems/truncate-sentence/

# Solution
```c++
class Solution {
public:
    string truncateSentence(string s, int k) {

        /**
         * @tag: String Pointer
         *
         * TC: O(N), where
         *      N is the length of the string
         *
         * SC: O(1)
         */

        int n = s.length();
        int i = 0;

        while (i < n && k > 0) {
            if (s[i] == ' ') {
                --k;
            }
            ++i;
        }

        return i == n ? s : s.substr(0, i - 1);
    }
};
```
