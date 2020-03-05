# Encoding

**Time Limit: 2000/1000 MS (Java/Others)    Memory Limit: 65536/32768 K (Java/Others)Total Submission(s): 60997    Accepted Submission(s): 27274**

Problem Description

Given a string containing only 'A' - 'Z', we could encode it using the following method:

\1. Each sub-string containing k same characters should be encoded to "kX" where "X" is the only character in this sub-string.

\2. If the length of the sub-string is 1, '1' should be ignored.

 



Input

The first line contains an integer N (1 <= N <= 100) which indicates the number of test cases. The next N lines contain N strings. Each string consists of only 'A' - 'Z' and the length is less than 10000.

 



Output

For each test case, output the encoded string in a line.

 



Sample Input

```
2
ABC
ABBCCC
```

 



Sample Output

```
ABC
A2B3C
```

 



Author

ZHANG Zheng

 



Recommend

JGShining   |   We have carefully selected several similar problems for you:  [1021](http://acm.hdu.edu.cn/showproblem.php?pid=1021) [1062](http://acm.hdu.edu.cn/showproblem.php?pid=1062) [1032](http://acm.hdu.edu.cn/showproblem.php?pid=1032) [1039](http://acm.hdu.edu.cn/showproblem.php?pid=1039) [1073](http://acm.hdu.edu.cn/showproblem.php?pid=1073) 





Accepted Code

```java
package cn.edu.hdu.acm;

import java.util.Scanner;

public class Main1020 {
	
	public static void main(String[] args) {
		Scanner scanner = new Scanner(System.in);
		int K = scanner.nextInt();
		for (int i = 1; i <= K; i++) {
			String s = scanner.next();
			// 记录字符串第一个字符
			char temp = s.charAt(0);
			// 计数
			int count = 1; 
			for (int j = 1; j < s.length(); j++) {
				if (s.charAt(j) != temp) {		
					if ( count == 1) {
						System.out.print(s.charAt(j - 1));
					}
					else {
						System.out.print(count);
						System.out.print(s.charAt(j - 1));			
						count = 1;
					}			
					temp = s.charAt(j);	
				}
				else {
					count++;
				}
				if (j == s.length()-1) {
					if (count == 1) {
						System.out.print(s.charAt(j));
					}
					else {
						System.out.print(count);
						System.out.print(s.charAt(j - 1));
					}		
				}
			}
		System.out.println();
		}	
	}
}
```

