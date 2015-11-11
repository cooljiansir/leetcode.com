[5 Longest Palindromic Substring](https://leetcode.com/problems/longest-palindromic-substring/)
```cpp
class Solution {
/*
*
*
*
* array: 0 1 2 3 4 5 6 7 8
* axis： |||||||||||||||||
*/
public:
    string longestPalindrome(string s) {
        int maxa,mmax=0;
        if(s.size()==0)return s;
        for(int i = 0;i<2*s.size();i++){
            for(int a=i/2,b=(i+1)/2;a>=0&&b<s.size()&&s[a]==s[b];a--,b++)
                if(b-a+1>mmax)
                    mmax = b-a+1,maxa=a;
        }
        return s.substr(maxa,mmax);
    }
};
```
