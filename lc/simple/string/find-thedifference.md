读题还是得认真啊
```c++
class Solution {
public:
    char findTheDifference(string s, string t) {
        int c[27]={0};
        for(char cc:t){
            c[cc-'a']++;
        }
        for(char cc:s){
            c[cc-'a']--;
        }
        for(int i=0;i<26;i++)
            {
                if(c[i]){
                    return char(i+'a');
            }
        }
        return 0;
    }
};
```