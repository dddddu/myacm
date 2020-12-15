从后往前扫

```c++
class Solution {
public:
    int lengthOfLastWord(string s) {
        int cnt=0;
        for(int i=s.length()-1;i>=0;i--){
            if(s[i]!=' '){
                while(s[i]!=' '&&i>=0)
                   {
                       cnt++;
                       i--;
                   } 
                break;
            }
        }
        return cnt;
    }
};
```