具体算作一个 贪心+双指针
```c++
class Solution {
public:
    int maxArea(vector<int>& height) {
       int ans=0;
        int l=0,r=height.size()-1;
        //ans=min(height(l),height(r))*(r-l);
        while(l!=r){
            //ans=max(ans,min(height[l],height[r])*(r-l));
            if(height[l]>height[r]){
                ans=max(ans,height[r]*(r-l));
                r--;
            }
            else{
                ans=max(ans,height[l]*(r-l));
                l++;
            }
        }
        return ans;
    }
};
```