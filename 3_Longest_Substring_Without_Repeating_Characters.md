##[3 Longest Substring Without Repeating Characters](https://leetcode.com/problems/longest-substring-without-repeating-characters/)
```cpp
class Solution {
public:
    int lengthOfLongestSubstring(string s) {
        map<char,int> mmap;
        int mmax = 0;
        int premax = 0;
        for(int i = 0;i<s.size();i++){
            if(mmap.find(s.at(i))==mmap.end()||(i-mmap[s.at(i)])>premax)
                premax++;
            else
                premax = i-mmap[s.at(i)];
            mmap[s.at(i)] = i;
            if(premax>mmax)mmax = premax;
        }
        return mmax;
    }
};
```
