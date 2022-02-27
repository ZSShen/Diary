
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
         */
         * TC: O(N),
         *     where N is the length of the string.
         *
         * SC: O(N)
         */

        int i = 0, n = word.length();
        unordered_set<string> set;

        while (i < n) {

            while (i < n && !isdigit(word[i])) {
                ++i;
            }

            if (i == n) {
                break;
            }

            string num;
            while (i < n && isdigit(word[i])) {
                if (!(num.empty() && word[i] == '0')) {
                    num.push_back(word[i++]);
                } else {
                    ++i;
                }
            }

            // Treat empty string as 0.
            set.emplace(move(num));
        }

        return set.size();
    }
};

```