不仔细读题 懒得测样例 多贡献了两发罚时 QAQ
```c++
class Solution {
public:
    int lengthOfLongestSubstring(string s) {
        int vis[300];
        for(int i=0;i<300;i++)
            vis[i]=-1;
        int ans=0;
        int be=-1;
        for(int i=0;i<s.length();i++){
            if(vis[s[i]]>be)
                be=vis[s[i]];
            if(i-be>ans)
                ans=i-be;
            vis[s[i]]=i;
        }
        return ans;
    }
};
```