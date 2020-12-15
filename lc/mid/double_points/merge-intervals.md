
双指针+排序

```c++
class Solution {
public:
    
    vector<vector<int>> merge(vector<vector<int>>& intervals) {
        vector<vector<int>> ans;
        int a,b;
        sort(intervals.begin(),intervals.end());
        int now=0;
        while(now<intervals.size()){
            a=intervals[now][0];
            b=intervals[now][1];
            now++;
            while(now<intervals.size()&&b>=intervals[now][0]){
                if(intervals[now][1]>b)
                    b=intervals[now][1];
                now++;
            }
            ans.push_back({a,b});
        }
        return ans;
    }
};
```