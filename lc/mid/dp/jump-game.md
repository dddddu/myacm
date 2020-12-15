Dp线性扫一遍
```c++
class Solution {
public:
    bool canJump(vector<int>& nums) {
        bool flag=true;
        for(int i=1;i<nums.size();i++)
        {
            if(nums[i-1]<i)
            {
                flag=false;
                break;
            }
            nums[i]+=i;
            if(nums[i-1]>nums[i])
                nums[i]=nums[i-1];
        }
        return flag;
    }
};
```