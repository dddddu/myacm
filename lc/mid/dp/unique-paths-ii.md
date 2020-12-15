多了个特判[[1]]的情况 这个样例感觉有点争议性 

```c++
class Solution {
public:
    int uniquePathsWithObstacles(vector<vector<int>>& obstacleGrid)     {
        int dp[102][102];
        int m=obstacleGrid.size();
        int n=obstacleGrid[0].size();
        dp[0][0]=obstacleGrid[0][0]^1;
        for(int i=1;i<n;i++){
           dp[0][i]= obstacleGrid[0][i]==1?0:dp[0][i-1];
        }
        for(int i=1;i<m;i++){
            dp[i][0]=obstacleGrid[i][0]==1?0:dp[i-1][0];
        }
        for(int i=1;i<m;i++){
            for(int j=1;j<n;j++){
                dp[i][j]=(obstacleGrid[i][j]==1?0:dp[i-1][j]+dp[i][j-1]);
            }
        }
        return dp[m-1][n-1];
    }
};
```