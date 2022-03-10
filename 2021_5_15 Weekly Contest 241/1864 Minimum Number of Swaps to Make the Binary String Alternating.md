
# Problem
### LeetCode 1864. Minimum Number of Swaps to Make the Binary String Alternating
https://leetcode.com/problems/minimum-number-of-swaps-to-make-the-binary-string-alternating/

# Solution
```c++
class Solution {
public:
    int minSwaps(string s) {

        /**
         * @tag: String, Greedy
         *
         * TC: O(N), where
         *      N is the string length
         *
         * SC: O(1)
         */

        int count_0 = 0, count_1 = 0;
        for (char ch : s) {
            if (ch == '0') {
                ++count_0;
            } else {
                ++count_1;
            }
        }

        if (abs(count_0 - count_1) > 1) {
            return -1;
        }

        if (count_0 > count_1) {
            // We should put 0s at the even indexes
            return countSwaps(s, '0');
        }
        if (count_1 > count_0) {
            // We should put 1s at the even indexes
            return countSwaps(s, '1');
        }

        return min(countSwaps(s, '0'), countSwaps(s, '1'));
    }

private:
    int countSwaps(const string& s, char target) {

        int cost = 0;

        for (char ch : s) {
            if (ch != target) {
                ++cost;
            }
            target = '0' + ('1' - target);
        }

        return cost / 2;
    }
};
```
