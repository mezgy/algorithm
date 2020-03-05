# Prime Ring Problem

**Time Limit: 4000/2000 MS (Java/Others)    Memory Limit: 65536/32768 K (Java/Others)Total Submission(s): 76951    Accepted Submission(s): 32586**

Problem Description

A ring is compose of n circles as shown in diagram. Put natural number 1, 2, ..., n into each circle separately, and the sum of numbers in two adjacent circles should be a prime.

Note: the number of first circle should always be 1.

![img](http://acm.hdu.edu.cn/data/images/1016-1.gif)

 



Input

n (0 < n < 20).

 



Output

The output format is shown as sample below. Each row represents a series of circle numbers in the ring beginning from 1 clockwisely and anticlockwisely. The order of numbers must satisfy the above requirements. Print solutions in lexicographical order.

You are to write a program that completes above process.

Print a blank line after each case.

 



Sample Input

```
6
8
```

 



Sample Output

```
Case 1:
1 4 3 2 5 6
1 6 5 2 3 4

Case 2:
1 2 3 8 5 6 7 4
1 2 5 8 3 4 7 6
1 4 7 6 5 8 3 2
1 6 7 4 3 8 5 2
```

 



Source

[Asia 1996, Shanghai (Mainland China)](http://acm.hdu.edu.cn/search.php?field=problem&key=Asia+1996%2C+Shanghai+(Mainland+China)&source=1&searchmode=source)

 



Recommend

JGShining   |   We have carefully selected several similar problems for you:  [1241](http://acm.hdu.edu.cn/showproblem.php?pid=1241) [1312](http://acm.hdu.edu.cn/showproblem.php?pid=1312) [1072](http://acm.hdu.edu.cn/showproblem.php?pid=1072) [1242](http://acm.hdu.edu.cn/showproblem.php?pid=1242) [1175](http://acm.hdu.edu.cn/showproblem.php?pid=1175) 





Accepted Code

```java
package cn.edu.hdu.acm;

import java.util.*;

public class Main1016 {
	public static int n;
	public static boolean[] prime = new boolean[50];   //标记数字是否是素数
	public static boolean[] vis = new boolean[25];     //标记数字是否填过
	public static int[] ans = new int[25];      //纪录路径
	public static boolean p ;
	public static void get_prime(){           //写素数筛
		Arrays.fill(prime, false);
		prime[2]=true;
		for(int i=2;i<50;i++){
			boolean flog = true;
			for(int j=2;j*j<=i;j++){
				if(i%j==0){
					flog = false;
					break;
				}
			}
			if(flog){
				prime[i] = true; 
			}
		}
	}
	
	public static void main(String[] args){
		int cnt=0;
		Scanner sc = new Scanner(System.in);
		get_prime();
		while(sc.hasNext()){
			cnt++;
			n = sc.nextInt();
			Arrays.fill(vis, false);
            Arrays.fill(ans, 0);
            ans[1] = 1;
			p = false;
			System.out.println("Case "+cnt+":");
			DFS(2);
			System.out.println();
		}
	}
	
	public static void DFS(int dig){
		if(dig>n){
			if(prime[ans[dig-1]+1]){
				for(int i=1;i<=n;i++){
					if(i<n){
						System.out.print(ans[i]+" ");
					}else{
						System.out.println(ans[i]);
					}
				}
			}
			return ;
		}
		for(int i=2;i<=n;i++){
			if(!vis[i] && prime[i+ans[dig-1]]){
				vis[i] = true;
				ans[dig] = i;
				DFS(dig+1);
				vis[i] = false;
			}
		}
	}
}

```

