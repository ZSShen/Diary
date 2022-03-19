
# Problem
### LeetCode 1897. Redistribute Characters to Make All Strings Equal
https://leetcode.com/problems/redistribute-characters-to-make-all-strings-equal/

# Solution
```c++
class Solution {
public:
    bool makeEqual(vector<string>& words) {

        /**
         * @tag: Hash Table
         *
         * TC: O(W * L) where
         *      W is the number of words
         *      L is the averaged word length
         *
         * SC: O(1)
         */

        int n = words.size();

        vector<int> freq(26);
        for (const auto& word : words) {
            for (char ch : word) {
                ++freq[ch - 'a'];
            }
        }

        for (int f : freq) {
            if (f % n != 0) {
                return false;
            }
        }

        return true;
    }
};
```
