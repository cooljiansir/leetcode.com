##1 [Two Sum](https://leetcode.com/problems/two-sum/)
```cpp
class Solution {
public:
    vector<int> twoSum(vector<int>& nums, int target) {
        vector<int> res;
        map<int,int> mmap;
        for(int i = 0;i<nums.size();i++){
            //record every number's index 
            mmap[nums[i]] = i;
        }
        for(int i = 0;i<nums.size();i++){
            int b = target - nums[i];
            map<int,int>::iterator it = mmap.find(b);
            if(it!=mmap.end()&&it->second!=i){
                res.push_back(i + 1);
                res.push_back(it->second + 1);
                return res;
            }
        }
        return res;
    }
};
```
