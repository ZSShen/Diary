
# Problem
### LeetCode 1805. Number of Different Integers in a String
https://leetcode.com/problems/number-of-different-integers-in-a-string/

# Solution

```c++
class Solution {
public:
    int numDifferentIntegers(string word) {

        /**
         * @tag: String Pointer
         *
         * TC: O(N),
         *     where N is the length of the string
         *
         * SC: O(N)
         */

        unordered_set<string> set;

        int n = word.length();
        int i = 0;

        while (i < n) {
            if (!isdigit(word[i])) {
                ++i;
                continue;
            }

            string num;
            while (i < n && isdigit(word[i])) {
                if (!(num.empty() && word[i] == '0')) {
                    num.push_back(word[i]);
                }
                ++i;
            }
            set.emplace(num);
        }

        return set.size();
    }
};
```