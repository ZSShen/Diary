
# Problem
### LeetCode 1898. Maximum Number of Removable Characters
https://leetcode.com/problems/maximum-number-of-removable-characters/

# Solution
```c++
class Solution {
public:
    int maximumRemovals(string s, string p, vector<int>& removable) {

        int ls = s.length();
        vector<int> reverse_index(ls, ls);

        int n = removable.size();
        for (int i = 0 ; i < n ; ++i) {
            reverse_index[removable[i]] = i;
        }

        int l = 0, r = n - 1;
        while (l + 1 < r) {
            int m = l + (r - l) / 2;
            if (helper(s, p, reverse_index, m)) {
                l = m;
            } else {
                r = m;
            }
        }

        if (helper(s, p, reverse_index, r)) {
            return r + 1;
        }
        if (helper(s, p, reverse_index, l)) {
            return l + 1;
        }
        return 0;
    }

private:
    bool helper(
        const string& s, const string& p,
        const vector<int>& reverse_index, int k) {

        int ls = s.length();
        int lp = p.length();
        int j = 0;

        for (int i = 0 ; i < ls && j < lp ; ++i) {
            if (reverse_index[i] <= k) {
                continue;
            }

            if (s[i] == p[j]) {
                ++j;
            }
        }

        return lp == j;
    }
};
```
