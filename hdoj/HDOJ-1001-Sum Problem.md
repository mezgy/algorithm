# Sum Problem

**Time Limit: 1000/500 MS (Java/Others)    Memory Limit: 65536/32768 K (Java/Others)Total Submission(s): 637240    Accepted Submission(s): 161358**

Problem Description

Hey, welcome to HDOJ(Hangzhou Dianzi University Online Judge).

In this problem, your task is to calculate SUM(n) = 1 + 2 + 3 + ... + n.

 



Input

The input will consist of a series of integers n, one integer per line.

 



Output

For each case, output SUM(n) in one line, followed by a blank line. You may assume the result will be in the range of 32-bit signed integer.

 



Sample Input

```
1
100
```

 



Sample Output

```
1

5050
```

 



Author

DOOM III

 



Recommend

We have carefully selected several similar problems for you:  [1002](http://acm.hdu.edu.cn/showproblem.php?pid=1002) [1090](http://acm.hdu.edu.cn/showproblem.php?pid=1090) [1003](http://acm.hdu.edu.cn/showproblem.php?pid=1003) [1091](http://acm.hdu.edu.cn/showproblem.php?pid=1091) [1004](http://acm.hdu.edu.cn/showproblem.php?pid=1004) 





Accepted Code

```java
package cn.edu.hdu.acm;

import java.util.Scanner;

public class Main1001 {
	public static void main(String[] args) {
		Scanner scanner = new Scanner(System.in);
		while(scanner.hasNext()){
			int n = scanner.nextInt();
			if(n % 2 == 0){
				int sum = n/2 * (n + 1);
				System.out.println(sum);
				System.out.println();
			}else{
				int sum = (n + 1) /2 *n;
				System.out.println(sum);
				System.out.println();
			}
		}
	}
}
```

