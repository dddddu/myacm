排序+双指针， 先排序，然后确定一个i 从i的后边开始双指针找 可以避免重复
```c++
class Solution {
public:
    
    vector<vector<int>> threeSum(vector<int>& nums) {
        vector<vector<int> > ans;
       if(nums.size()<3)
            return ans;
        sort(nums.begin(),nums.end());
        for(int i=0;i<nums.size()-2;i++){
            if( nums[i]>0)
                break;
            if(i!=0&&nums[i]==nums[i-1])
                continue;
            int l=i+1,r=nums.size()-1;
            while(l<r){
                if(nums[l]+nums[r]==-nums[i]){
                   vector<int> tmp;
                   tmp.push_back(nums[i]);
                   tmp.push_back(nums[l]);
                   tmp.push_back(nums[r]);     
                    ans.push_back(tmp);
                    l++;
                    while(l<r&&nums[l]==nums[l-1])
                        l++;
                    r--;
                    while(r>l&&nums[r]==nums[r+1])
                        r--;
                }else{
                    if(nums[l]+nums[r]>-nums[i]){
                        r--;
                    }else{
                        l++;
                    }
                    continue;
                }
            }
        }
        return ans;
    }
};
```