
# Problem
### LeetCode 1871. Jump Game VII
https://leetcode.com/problems/jump-game-vii/

# Solution
```c++
class Solution {
public:
    bool canReach(string s, int min_jump, int max_jump) {

        /**
         * @tag: BFS
         *
         * TC: O(N), where
         *      N is the number of cells
         *
         * SC: O(N)
         */


        int n = s.length();
        int cur_max = 0;

        s[0] = '1';
        queue<int> queue;
        queue.emplace(0);

        while (!queue.empty()) {
            int src = queue.front();
            queue.pop();

            if (src == n - 1) {
                return true;
            }

            int lo = max(src + min_jump, cur_max);
            int hi = min(src + max_jump, n - 1);

            for (int dst = lo ; dst <= hi ; ++dst) {
                if (s[dst] == '1') {
                    continue;
                }

                queue.emplace(dst);
                s[dst] = '1';
            }

            cur_max = min(n - 1, hi);
        }

        return false;
    }
};
```
