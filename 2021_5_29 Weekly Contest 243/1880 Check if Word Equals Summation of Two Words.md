
# Problem
### LeetCode 1880. Check if Word Equals Summation of Two Words
https://leetcode.com/problems/check-if-word-equals-summation-of-two-words/

# Solution
```c++
class Solution {
public:
    bool isSumEqual(string first_word, string second_word, string target_word) {

        auto first = convert(first_word);
        auto second = convert(second_word);
        auto target = convert(target_word);

        return first + second == target;
    }

private:
    long convert(const string &s) {

        string copy(s);

        for (char& ch : copy) {
            ch = ch - 'a' + '0';
        }

        return stol(copy);
    }
};
```
