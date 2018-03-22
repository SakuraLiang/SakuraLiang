# 题目
机器人位于一个 m x n 网格的左上角, 在下图中标记为“Start” (开始)。

机器人每次只能向下或者向右移动一步。机器人试图达到网格的右下角，在下图中标记为“Finish”(结束)。

问有多少条不同的路径？
# 解法




```ruby
class Solution {
public:
      int uniquePaths(int m, int n) {
        vector<vector<int> > path(m, vector<int>(n, 1));
        for(int i = 1; i < m; i ++)
        {
            for(int j = 1; j < n; j ++)
            {
                path[i][j] = path[i-1][j] + path[i][j-1];
            }
        }
        return path[m-1][n-1];
    }
};

```
# 分析
采用动态规划。这一步的路径总和是上一步两种可能的总和。建立动态二维数组用来存储每一个位置的个数。还有一种是利用组合排列的方法，也是我之前想到的，但是写出的代码却不能通过所有的例子。
