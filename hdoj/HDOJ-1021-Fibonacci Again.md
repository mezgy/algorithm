# Fibonacci Again

**Time Limit: 2000/1000 MS (Java/Others)    Memory Limit: 65536/32768 K (Java/Others)Total Submission(s): 82886    Accepted Submission(s): 37465**

Problem Description

There are another kind of Fibonacci numbers: F(0) = 7, F(1) = 11, F(n) = F(n-1) + F(n-2) (n>=2).

 



Input

Input consists of a sequence of lines, each containing an integer n. (n < 1,000,000).

 



Output

Print the word "yes" if 3 divide evenly into F(n).

Print the word "no" if not.

 



Sample Input

```
0
1
2
3
4
5
```

 



Sample Output

```
no
no
yes
no
no
no
```

 



Author

Leojay

 



Recommend

JGShining   |   We have carefully selected several similar problems for you:  [1061](http://acm.hdu.edu.cn/showproblem.php?pid=1061) [1108](http://acm.hdu.edu.cn/showproblem.php?pid=1108) [1071](http://acm.hdu.edu.cn/showproblem.php?pid=1071) [1049](http://acm.hdu.edu.cn/showproblem.php?pid=1049) [1032](http://acm.hdu.edu.cn/showproblem.php?pid=1032) 





Acceptet Code

```java
//通过对各项除3取余发现每8项是一个循环
package cn.edu.hdu.acm;

import java.util.Scanner;

public class Main1021 {
	
	public static int fib(int n) {
		n = n % 8;
		if (n == 0) return 7;
		if (n == 1) return 11;
		else {
			int[] lala = new int[n+1];
			lala[0] = 7;
			lala[1] = 11;
			for (int i = 2; i <= n; i++) {
				lala[i] = lala[i-1] + lala[i-2];
			}
			return lala[n];
		}
	}
	
	public static void main(String[] args) {
		Scanner scanner = new Scanner(System.in);	
		while (scanner.hasNext()) {
			int k = scanner.nextInt();
			int result = fib(k) % 3;	
			if (result == 0)
				System.out.println("yes");
			else
				System.out.println("no");		
		}
	}
}

```

