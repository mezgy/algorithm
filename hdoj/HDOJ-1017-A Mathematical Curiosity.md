# A Mathematical Curiosity

**Time Limit: 2000/1000 MS (Java/Others)    Memory Limit: 65536/32768 K (Java/Others)Total Submission(s): 54134    Accepted Submission(s): 17599**

Problem Description

Given two integers n and m, count the number of pairs of integers (a,b) such that 0 < a < b < n and (a^2+b^2 +m)/(ab) is an integer.

This problem contains multiple test cases!

The first line of a multiple input is an integer N, then a blank line followed by N input blocks. Each input block is in the format indicated in the problem description. There is a blank line between input blocks.

The output format consists of N output blocks. There is a blank line between output blocks.

 



Input

You will be given a number of cases in the input. Each case is specified by a line containing the integers n and m. The end of input is indicated by a case in which n = m = 0. You may assume that 0 < n <= 100.

 



Output

For each case, print the case number as well as the number of pairs (a,b) satisfying the given property. Print the output for each case on one line in the format as shown below.

 



Sample Input

```
1

10 1
20 3
30 4
0 0
```

 



Sample Output

```
Case 1: 2
Case 2: 4
Case 3: 5
```

 



Source

[East Central North America 1999, Practice](http://acm.hdu.edu.cn/search.php?field=problem&key=East+Central+North+America+1999%2C+Practice&source=1&searchmode=source)

 



Recommend

JGShining   |   We have carefully selected several similar problems for you:  [1018](http://acm.hdu.edu.cn/showproblem.php?pid=1018) [1021](http://acm.hdu.edu.cn/showproblem.php?pid=1021) [1019](http://acm.hdu.edu.cn/showproblem.php?pid=1019) [1032](http://acm.hdu.edu.cn/showproblem.php?pid=1032) [1020](http://acm.hdu.edu.cn/showproblem.php?pid=1020) 





Accepted Code

```java
package cn.edu.hdu.acm;

import java.util.*;
 
public class Main1017 {
	
	public static void main(String[] args) {
		Scanner input = new Scanner(System.in);
		int i = 0;
		int t = input.nextInt();
		for (i = 0; i < t; i++) {
			int cas = 1;
			while (true) {
				int n = input.nextInt();
				int m = input.nextInt();
				int ans = 0;
				if (n == 0 && m == 0)
					break;
				for (int a = 1; a < n; a++) {
					for (int b = a + 1; b < n; b++) {
						if ((a * a + b * b + m) % (a * b) == 0) {
							ans++;
						}
					}
				}
				System.out.println("Case " + cas + ": " + ans);
				cas++;
			}
			if (i != t - 1) {
				System.out.println();
			}
		}
	}
}

```

