# N!

**Time Limit: 10000/5000 MS (Java/Others)    Memory Limit: 262144/262144 K (Java/Others)Total Submission(s): 101715    Accepted Submission(s): 30352**

Problem Description

Given an integer N(0 ≤ N ≤ 10000), your task is to calculate N!

 



Input

One N in one line, process to the end of file.

 



Output

For each N, output N! in one line.

 



Sample Input

```
1
2
3
```

 



Sample Output

```
1
2
6
```

 



Author

JGShining（极光炫影）

 



Recommend

We have carefully selected several similar problems for you:  [1715](http://acm.hdu.edu.cn/showproblem.php?pid=1715) [1047](http://acm.hdu.edu.cn/showproblem.php?pid=1047) [1063](http://acm.hdu.edu.cn/showproblem.php?pid=1063) [1753](http://acm.hdu.edu.cn/showproblem.php?pid=1753) [1316](http://acm.hdu.edu.cn/showproblem.php?pid=1316) 





Accepted Code

```java
package cn.edu.hdu.acm;

import java.util.Scanner;
import java.math.BigInteger;

public class Main1042 {

        public static void main(String[] args) {
            Scanner in =new Scanner (System.in);
            while(in.hasNext())
            {
                int n=in.nextInt();
                BigInteger sum=BigInteger.ONE;
                for(int i=1;i<=n;i++)
                {
                    sum=sum.multiply(BigInteger.valueOf(i));
                }
                System.out.println(sum);
            }
        }
    }

```

