```C
#include<iostream>
#include<cstdio>
#include<cstring>
#include<cmath>
using namespace std;
int a[100010];
int dp[100010];
int max(int x,int y){return x>y?x:y;}
int main()
{
 int k;
 int i;
 scanf("%d",&k);
 for(i=0;i<k;i++)
 {
  scanf("%d",&a[i]);
 }
 memset(dp,0,sizeof(dp));//初始化dp
 dp[0]=a[0];
 for(i=1;i<k;i++)
 {
  dp[i]=max(0,dp[i-1])+a[i];
 }
 int ans=dp[0];
 for(i=0;i<k;i++)
 {
  if(ans<dp[i]){ans=dp[i];}
 }
 printf("%d\n",ans);
 return 0;
}
```

## 1.定义状态：

记数组中以第 i 个元素结尾的连续子数组的最大和为 dp[i] (0 ≤ i < numsSize);

## 2.状态转移方程：

若 dp[i - 1] > = 0，其中 i >= 1，则将 nums[i] 加入到 dp[i - 1] 中，使得连续子数组的和能继续增大；

否则，就抛弃 dp[i - 1]（i >= 1），从第 i 个元素 nums[i] 开始重新寻找最大和的连续子数组。

因此，转移方程: dp[i] = max{dp[i - 1] + nums[i], nums[i]} ;

## 3.边界条件：

dp[0] = nums[0] 。

## 4.复杂度：
时间复杂度O(n)
空间复杂度O(n) 可优化为O(1)


| Personal Software Process Stages | 个人软件流程阶段 | 估计的时间（分钟）| 实际花费的时间 (分钟) |
|  :----------------------------------:  |  :----------------:  | :------------------:  | :---------------------:  |
| Planning | 计划-把工作细化并大致安排次序 | 5| 6 |
| Development| 开发 | 20| 30|
| Analysis |  需求分析(包括学习新技术)   | 10| 25 |
| Design Spec | 生成设计文档 | 8| 5 |
| Design Review | 设计复审(和同事审核设计文档) | 5| 5 |
| Coding Standard | 代码规范 (制定合适的规范) | 5| 5 |
| Design| 具体设计| 20 | 20 |
| Coding| 具体编码 | 5| 5 |
| Code Review | 代码复审 | 5| 5 |
| Test| 测试（自我测试，修改代码，提交修改）| 10| 8 |
| Reporting| 总结报告 | 10| 20 |
| Test Report| 个人软件流程阶段 | 5| 5 |
|Size Measurement| 计算工作量 | 5 | 3 |
| Postmortem & Improvement Plan| 事后总结, 并提出改进 | 10| 15 |
| Total 总计 |123 |157  |




