
# Problem
### LeetCode 1832. Check if the Sentence Is Pangram
https://leetcode.com/problems/check-if-the-sentence-is-pangram/

# Solution
```c++
class Solution {
public:
    bool checkIfPangram(string s) {

        /**
         * TC: O(N), where
         *      N is the length of the string
         *
         * SC: O(1)
         */

        vector<bool> map(26);

        for (char c : s) {
            map[c - 'a'] = true;
        }

        return count(map.begin(), map.end(), true) == 26;
    }
};
```
