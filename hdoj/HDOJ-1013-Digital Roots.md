# Digital Roots

**Time Limit: 2000/1000 MS (Java/Others)    Memory Limit: 65536/32768 K (Java/Others)Total Submission(s): 101914    Accepted Submission(s): 31712**

Problem Description

The digital root of a positive integer is found by summing the digits of the integer. If the resulting value is a single digit then that digit is the digital root. If the resulting value contains two or more digits, those digits are summed and the process is repeated. This is continued as long as necessary to obtain a single digit.

For example, consider the positive integer 24. Adding the 2 and the 4 yields a value of 6. Since 6 is a single digit, 6 is the digital root of 24. Now consider the positive integer 39. Adding the 3 and the 9 yields 12. Since 12 is not a single digit, the process must be repeated. Adding the 1 and the 2 yeilds 3, a single digit and also the digital root of 39.

 



Input

The input file will contain a list of positive integers, one per line. The end of the input will be indicated by an integer value of zero.

 



Output

For each integer in the input, output its digital root on a separate line of the output.

 



Sample Input

```
24
39
0
```

 



Sample Output

```
6
3
```

 



Source

[Greater New York 2000](http://acm.hdu.edu.cn/search.php?field=problem&key=Greater+New+York+2000&source=1&searchmode=source)

 



Recommend

We have carefully selected several similar problems for you:  [1017](http://acm.hdu.edu.cn/showproblem.php?pid=1017) [1021](http://acm.hdu.edu.cn/showproblem.php?pid=1021) [1018](http://acm.hdu.edu.cn/showproblem.php?pid=1018) [1048](http://acm.hdu.edu.cn/showproblem.php?pid=1048) [1020](http://acm.hdu.edu.cn/showproblem.php?pid=1020) 





Accepted Code

```java
package cn.edu.hdu.acm;

import java.math.BigInteger;
import java.util.Scanner;

public class Main1013 {
	public static void main(String[] args) {
		Scanner scanner = new Scanner(System.in);
		BigInteger b;
		
		while (scanner.hasNext()) {
			b = scanner.nextBigInteger();
			if (b.intValue()==0) {
				break;
			} else if (b.mod(new BigInteger(String.valueOf(9))).intValue()==0){
				System.out.println(9);
			} else {
				System.out.println(b.mod(new BigInteger(String.valueOf(9))));
			}
		}
	}
}

```

