
# Problem
### LeetCode 1865. Finding Pairs With a Certain Sum
https://leetcode.com/problems/finding-pairs-with-a-certain-sum/

# Solution
```c++
class FindSumPairs {
public:
    FindSumPairs(vector<int>& nums1, vector<int>& nums2)
        : nums2(nums2) {

        for (int e : nums1) {
            ++map1[e];
        }
        for (int e : nums2) {
            ++map2[e];
        }
    }

    void add(int index, int val) {

        int num = nums2[index];
        --map2[num];

        if (map2[num] == 0) {
            map2.erase(num);
        }

        nums2[index] += val;
        ++map2[nums2[index]];
    }

    int count(int tot) {
        int sum = 0;

        for (const auto& kv : map1) {
            int k = kv.first, v = kv.second;
            sum += v * map2[tot - k];
        }

        return sum;
    }

private:
    vector<int> nums2;
    unordered_map<int, int> map1, map2;
};

/**
 * Your FindSumPairs object will be instantiated and called as such:
 * FindSumPairs* obj = new FindSumPairs(nums1, nums2);
 * obj->add(index,val);
 * int param_2 = obj->count(tot);
 */
```
