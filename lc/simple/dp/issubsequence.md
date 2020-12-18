虽然是个dp的tag但是感觉还是双指针更快

```c++
class Solution {
public:
    bool isSubsequence(string s, string t) {
        bool flag=false;
        int j=0;
        int i=0;
        for(j=0;j<t.length();j++){
            if(i==s.length())
                break;
            if(s[i]==t[j]){
                i++;
            }
        }
        if(i==s.length())
            flag=true;
        return flag;
    }
};
```