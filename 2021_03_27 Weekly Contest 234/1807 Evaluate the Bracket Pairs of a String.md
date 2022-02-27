
# Problem
### LeetCode 1807. Evaluate the Bracket Pairs of a String
https://leetcode.com/problems/finding-the-users-active-minutes/

# Solution
```c++
class Solution {
public:
    string evaluate(string s, vector<vector<string>>& knowledge) {

        /**
         * @tag: String Pointer, Hash Table
         *
         * TC: O(N), where
         *      N is the length of the string
         *
         * SC: O(N)
         */

        unordered_map<string, string> map;
        for (const auto& kv : knowledge) {
            map[kv[0]] = kv[1];
        }

        int n = s.length(), i = 0;
        string res;

        while (i < n) {
            if (s[i] != '(' && s[i] != ')') {
                res.push_back(s[i++]);
                continue;
            }

            ++i;
            string key;
            while (s[i] != ')') {
                key.push_back(s[i++]);
            }

            if (map.count(key) == 1) {
                res += map[key];
            } else {
                res.push_back('?');
            }

            ++i;
        }

        return res;
    }
};
```
