# Starship Troopers

**Time Limit: 10000/5000 MS (Java/Others)    Memory Limit: 65536/32768 K (Java/Others)Total Submission(s): 29359    Accepted Submission(s): 6748**

Problem Description

You, the leader of Starship Troopers, are sent to destroy a base of the bugs. The base is built underground. It is actually a huge cavern, which consists of many rooms connected with tunnels. Each room is occupied by some bugs, and their brains hide in some of the rooms. Scientists have just developed a new weapon and want to experiment it on some brains. Your task is to destroy the whole base, and capture as many brains as possible.

To kill all the bugs is always easier than to capture their brains. A map is drawn for you, with all the rooms marked by the amount of bugs inside, and the possibility of containing a brain. The cavern's structure is like a tree in such a way that there is one unique path leading to each room from the entrance. To finish the battle as soon as possible, you do not want to wait for the troopers to clear a room before advancing to the next one, instead you have to leave some troopers at each room passed to fight all the bugs inside. The troopers never re-enter a room where they have visited before.

A starship trooper can fight against 20 bugs. Since you do not have enough troopers, you can only take some of the rooms and let the nerve gas do the rest of the job. At the mean time, you should maximize the possibility of capturing a brain. To simplify the problem, just maximize the sum of all the possibilities of containing brains for the taken rooms. Making such a plan is a difficult job. You need the help of a computer.

 



Input

The input contains several test cases. The first line of each test case contains two integers N (0 < N <= 100) and M (0 <= M <= 100), which are the number of rooms in the cavern and the number of starship troopers you have, respectively. The following N lines give the description of the rooms. Each line contains two non-negative integers -- the amount of bugs inside and the possibility of containing a brain, respectively. The next N - 1 lines give the description of tunnels. Each tunnel is described by two integers, which are the indices of the two rooms it connects. Rooms are numbered from 1 and room 1 is the entrance to the cavern.

The last test case is followed by two -1's.

 



Output

For each test case, print on a single line the maximum sum of all the possibilities of containing brains for the taken rooms.

 



Sample Input

```
5 10
50 10
40 10
40 20
65 30
70 30
1 2
1 3
2 4
2 5
1 1
20 7
-1 -1
```

 



Sample Output

```
50
7
```

 



Author

XU, Chuan

 



Source

[ZJCPC2004](http://acm.hdu.edu.cn/search.php?field=problem&key=ZJCPC2004&source=1&searchmode=source)

 



Recommend

JGShining   |   We have carefully selected several similar problems for you:  [1561](http://acm.hdu.edu.cn/showproblem.php?pid=1561) [1203](http://acm.hdu.edu.cn/showproblem.php?pid=1203) [2955](http://acm.hdu.edu.cn/showproblem.php?pid=2955) [2415](http://acm.hdu.edu.cn/showproblem.php?pid=2415) [1059](http://acm.hdu.edu.cn/showproblem.php?pid=1059) 





Accepted Code

```java
package cn.edu.hdu.acm;

import java.util.ArrayList;
import java.util.Scanner;

public class Main1011 {

	private static int m;
	private static int n;
	private static Scanner scanner;
	private static int[][] dp;
	private static ArrayList<Integer>[] graph;
	private static int[][] arr;

public static void main(String[] args) {
	scanner = new Scanner(System.in);
	while (true) {
		n = scanner.nextInt();
		m = scanner.nextInt();
		if(n==-1&&m==-1)break;
			createGraph();
		if(m==0) {
		System.out.println(0);
		}
		else {
		dp = new int [n+1][m+1];
		dfs(1,0);
		System.out.println(dp[1][m]);
		}
	}
}

private static void dfs(int r,int p) {
	int a1 = (arr[r][0]+19)/20;
	for (int i = a1; i <=m; i++) {
		dp[r][i] = arr[r][1];
		}
	for (int i = 0; i < graph[r].size(); i++) {
		int h = graph[r].get(i);
		if (h!=p) {
		dfs(h,r);
		for (int j = m; j >=a1; j--) {
		for (int j2 = 1; j2 <= j-a1; j2++) {
			dp[r][j] = Math.max(dp[r][j], dp[h][j2]+dp[r][j-j2]);
			}
		}
		}
	}
}

private static void createGraph() {
	arr = new int [n+1][2];
	graph = new ArrayList [n+1];
	for (int i = 1; i <=n; i++) {
		arr[i][0] = scanner.nextInt();
		arr[i][1] = scanner.nextInt();
		}
	for (int i = 0; i < graph.length; i++) {
		graph[i] = new ArrayList<Integer>();
		}
	for (int i = 1; i < n; i++) {
		int a = scanner.nextInt();
		int b = scanner.nextInt();
		graph[a].add(b);
		graph[b].add(a);
		}
	}
}
```







