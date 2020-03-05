# Max Sum Plus Plus

**Time Limit: 2000/1000 MS (Java/Others)    Memory Limit: 65536/32768 K (Java/Others)Total Submission(s): 45062    Accepted Submission(s): 16339**

Problem Description

Now I think you have got an AC in Ignatius.L's "Max Sum" problem. To be a brave ACMer, we always challenge ourselves to more difficult problems. Now you are faced with a more difficult problem.

Given a consecutive number sequence S*1*, S*2*, S*3*, S*4* ... S*x*, ... S*n* (1 ≤ x ≤ n ≤ 1,000,000, -32768 ≤ S*x* ≤ 32767). We define a function sum(i, j) = S*i* + ... + S*j* (1 ≤ i ≤ j ≤ n).

Now given an integer m (m > 0), your task is to find m pairs of i and j which make sum(i*1*, j*1*) + sum(i*2*, j*2*) + sum(i*3*, j*3*) + ... + sum(i*m*, j*m*) maximal (i*x* ≤ i*y* ≤ j*x* or i*x* ≤ j*y* ≤ j*x* is not allowed).

But I`m lazy, I don't want to write a special-judge module, so you don't have to output m pairs of i and j, just output the maximal summation of sum(i*x*, j*x*)(1 ≤ x ≤ m) instead. ^_^

 



Input

Each test case will begin with two integers m and n, followed by n integers S*1*, S*2*, S*3* ... S*n*.
Process to the end of file.

 



Output

Output the maximal summation described above in one line.

 



Sample Input

```
1 3 1 2 3
2 6 -1 4 -2 3 -2 3
```

 



Sample Output

```
6
8

Hint
Huge input, scanf and dynamic programming is recommended.
 
```

 



Author

JGShining（极光炫影）

 



Recommend

We have carefully selected several similar problems for you:  [1074](http://acm.hdu.edu.cn/showproblem.php?pid=1074) [1025](http://acm.hdu.edu.cn/showproblem.php?pid=1025) [1081](http://acm.hdu.edu.cn/showproblem.php?pid=1081) [1080](http://acm.hdu.edu.cn/showproblem.php?pid=1080) [1160](http://acm.hdu.edu.cn/showproblem.php?pid=1160) 





Accepted Code

```java
package cn.edu.hdu.acm;

import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;
import java.io.StreamTokenizer;

//最开始没读懂题意，后来网上搜了才知道是n个数中找最大的不相交的m子段和，dp
//转移方程： cur[i,j]=max(cur[i,j-1]+a[j],cur[i-1,t]+a[j]) 表示前j项中最大的i个字段的最大和


  /*设状态为 cur[i,j]，表示前 j 项分为 i 段的最大和，且第 i 段必须包含 data[j]，则状态转移方程如下：
cur[i,j] = max{cur[i,j − 1] + data[j],max{cur[i − 1,t] + data[j]}}, 其中i ≤ j ≤ n,i − 1 ≤ t < j
target = max{cur[m,j]}, 其中m ≤ j ≤ n
分为两种情况：
• 情况一，data[j] 包含在第 i 段之中，cur[i,j − 1] + data[j]。
• 情况二，data[j] 独立划分成为一段，max{cur[i − 1,t] + data[j]}。
观察上述两种情况可知 cur[i,j] 的值只和 cur[i,j-1] 和 cur[i-1,t] 这两个值相关，因此不需要二维数组，
可以用滚动数组，只需要两个一维数组，用 cur[j] 表示现阶段的最大值，即 cur[i,j − 1] + data[j]，用
pre[j] 表示上一阶段的最大值，即 max{cur[i − 1,t] + data[j]}。*/

public class Main1024 {
	static final int maxn=(int)1e6+5;
	static int a[]=new int[maxn];
	
	static int max(int a,int b){
		return a>b?a:b;
	}
	public static void main(String[] args) throws IOException {
		StreamTokenizer st=new StreamTokenizer(new BufferedReader(new InputStreamReader(System.in)));
		int m,n;
		while(st.nextToken()!=StreamTokenizer.TT_EOF){
			m=(int)st.nval;
			st.nextToken();
			n=(int)st.nval;
			for(int i=1;i<=n;i++){
				st.nextToken();
				a[i]=(int)st.nval;
			}
			int cur[]=new int[n+1];//表示现阶段的最大值
			int pre[]=new int[n+1];//表示上一个阶段的最大值
			int j=0;
			int max_sum=0;
			for(int i=1;i<=m;i++){
				max_sum=-0x3f3f3f3f;
				for(j=i;j<=n;j++){
					cur[j]=max(cur[j-1]+a[j],pre[j-1]+a[j]);
					pre[j-1]=max_sum;//保存上一个阶段的最大值
					if(max_sum<cur[j]){
						max_sum=cur[j];//记录这个阶段的最大值
					}
				}
				pre[j-1]=max_sum;//保存上一个阶段的最大值，因为j++了，所以这里是j-1
			}
			System.out.println(max_sum);
		}
	}
}
```

