题目链接：http://www.lintcode.com/zh-cn/problem/unique-paths/#
不同的路径 查看运行结果 

有一个机器人的位于一个M×N个网格左上角（下图中标记为'Start'）。

机器人每一时刻只能向下或者向右移动一步。机器人试图达到网格的右下角（下图中标记为'Finish'）。
问有多少条不同的路径？
注意
n和m均不超过100

class Solution {
public:
    /**
     * @param n, m: positive integer (1 <= n ,m <= 100)
     * @return an integer
     */
    int C(int x, int y){
        long long ans = 1;
        x = x-y+1;
        for(int i=1; i<=y; ++i, ++x){
            ans *= x;
            ans /= i;
        }
        return (int)ans;
    }
    int uniquePaths(int m, int n) {
        // dp解法
        // int dp[m+1][n+1];
        // memset(dp, 0, sizeof(dp));
        // dp[1][1] = 1;
        // for(int i=1; i<=m; ++i)
        //     for(int j=1; j<=n; ++j)
        //         if(i!=1 || j!=1)
        //             dp[i][j] = dp[i-1][j]+dp[i][j-1];
        // return dp[m][n];
        
        
        //组合数学解法：无论怎么走，一共要走 m+n-2步，从m+n-2不中任选初m-1或者
        //n-1步的组合数，就是总共的路线数
        return C(m+n-2, min(n-1, m-1));
    }
};

