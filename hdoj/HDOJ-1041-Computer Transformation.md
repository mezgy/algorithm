# Computer Transformation

**Time Limit: 2000/1000 MS (Java/Others)    Memory Limit: 65536/32768 K (Java/Others)Total Submission(s): 10029    Accepted Submission(s): 3767**

Problem Description

A sequence consisting of one digit, the number 1 is initially written into a computer. At each successive time step, the computer simultaneously tranforms each digit 0 into the sequence 1 0 and each digit 1 into the sequence 0 1. So, after the first time step, the sequence 0 1 is obtained; after the second, the sequence 1 0 0 1, after the third, the sequence 0 1 1 0 1 0 0 1 and so on.

How many pairs of consequitive zeroes will appear in the sequence after n steps?

 



Input

Every input line contains one natural number n (0 < n ≤1000).

 



Output

For each input n print the number of consecutive zeroes pairs that will appear in the sequence after n steps.

 



Sample Input

```
2
3
```

 



Sample Output

```
1
1
```

 



Source

[Southeastern Europe 2005](http://acm.hdu.edu.cn/search.php?field=problem&key=Southeastern+Europe+2005&source=1&searchmode=source)

 



Recommend

JGShining   |   We have carefully selected several similar problems for you:  [1143](http://acm.hdu.edu.cn/showproblem.php?pid=1143) [1200](http://acm.hdu.edu.cn/showproblem.php?pid=1200) [1196](http://acm.hdu.edu.cn/showproblem.php?pid=1196) [1064](http://acm.hdu.edu.cn/showproblem.php?pid=1064) [1063](http://acm.hdu.edu.cn/showproblem.php?pid=1063) 





Accepted Code

```java
package cn.edu.hdu.acm;

import java.util.Scanner;
import java.math.BigInteger;

public class Main1041 {

    public static void main(String args[]) {
        Scanner cin = new Scanner(System.in);
        BigInteger []f = new BigInteger[1001];
        f[1] = new BigInteger("0");
        f[2] = new BigInteger("1");
        f[3] = new BigInteger("1");
        for (int i=4; i<1001; ++i) {
            if (i % 2 == 0) {
                f[i] = f[i-1].multiply(BigInteger.valueOf(2)).add(BigInteger.ONE);
            }
            else {
                f[i] = f[i-1].multiply(BigInteger.valueOf(2)).subtract(BigInteger.ONE);
            }
        }
        int n;
        while (cin.hasNextInt()) {
            n = cin.nextInt();
            System.out.println(f[n]);
        }
    }
}

```



 