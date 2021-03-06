##[4 Median of Two Sorted Arrays](https://leetcode.com/problems/median-of-two-sorted-arrays/)
```cpp
class Solution {
public:
/*
* 
*  # represents the samller half 
*  - means the bigger half
*
*                       xy     
* nums1:   ##############------     #:a 
*
*                 zw 
* nums2:       ####---------        #:(m+n+1)/2-a
* 
* we have:
* y and w and both bigger than x and z
* so y>=x and y>=z w>=z w>=x
* beacause they are sorted arrays 
* so y>=x and w>=z which we don't have to compare
* so only when y>=z && w>=x
* 
* 
* 
*/
    int at(int i,vector<int> &nums,int flag){
        if(flag==1)return nums[i];
        else return nums[nums.size()-i-1];
    }
    double findMedianSortedArrays(vector<int>& nums1, vector<int>& nums2) {
        int flag[]={1,1};
        if(nums1.size()>0&&nums1.back()<nums1.front())flag[0] = -1;
        if(nums2.size()>0&&nums2.back()<nums2.front())flag[1] = -1;
        //b-search
        int m = nums1.size();
        int n = nums2.size();
        int left = max(0,(m+n+1)/2-n);
        int right = min((m+n+1)/2,m);
        int a,b;
        while(left<=right){
            a = (left+right)/2;
            b = (m+n+1)/2-a;
            if(a<nums1.size()&&b>0&&at(a,nums1,flag[0])<at(b-1,nums2,flag[1]))
                left = a + 1;
            else if(a>0&&b<nums2.size()&&at(b,nums2,flag[1])<at(a-1,nums1,flag[0]))
                right = a - 1;
            else{
                int leftmax=-1<<30,rightmin=1<<30;
                if(a>0)leftmax = at(a-1,nums1,flag[0]);
                if(b>0)leftmax = max(leftmax,at(b-1,nums2,flag[1]));
                if(a<nums1.size())rightmin = at(a,nums1,flag[0]);
                if(b<nums2.size())rightmin = min(rightmin,at(b,nums2,flag[1]));
                if((m+n)%2==1)return leftmax;
                else return (leftmax + rightmin)/2.0;
            }
        }
    }
};
```
