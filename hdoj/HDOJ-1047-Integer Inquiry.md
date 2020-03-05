# Integer Inquiry

**Time Limit: 2000/1000 MS (Java/Others)    Memory Limit: 65536/32768 K (Java/Others)Total Submission(s): 28161    Accepted Submission(s): 8028**

Problem Description

One of the first users of BIT's new supercomputer was Chip Diller. He extended his exploration of powers of 3 to go from 0 to 333 and he explored taking various sums of those numbers.
``This supercomputer is great,'' remarked Chip. ``I only wish Timothy were here to see these results.'' (Chip moved to a new apartment, once one became available on the third floor of the Lemon Sky apartments on Third Street.)

 



Input

The input will consist of at most 100 lines of text, each of which contains a single VeryLongInteger. Each VeryLongInteger will be 100 or fewer characters in length, and will only contain digits (no VeryLongInteger will be negative).

The final input line will contain a single zero on a line by itself.

 



Output

Your program should output the sum of the VeryLongIntegers given in the input.


This problem contains multiple test cases!

The first line of a multiple input is an integer N, then a blank line followed by N input blocks. Each input block is in the format indicated in the problem description. There is a blank line between input blocks.

The output format consists of N output blocks. There is a blank line between output blocks.

 



Sample Input

```
1


123456789012345678901234567890
123456789012345678901234567890
123456789012345678901234567890
0
```

 



Sample Output

```
370370367037037036703703703670
```

 



Source

[East Central North America 1996](http://acm.hdu.edu.cn/search.php?field=problem&key=East+Central+North+America+1996&source=1&searchmode=source)

 



Recommend

We have carefully selected several similar problems for you:  [1063](http://acm.hdu.edu.cn/showproblem.php?pid=1063) [1316](http://acm.hdu.edu.cn/showproblem.php?pid=1316) [1715](http://acm.hdu.edu.cn/showproblem.php?pid=1715) [1753](http://acm.hdu.edu.cn/showproblem.php?pid=1753) [1060](http://acm.hdu.edu.cn/showproblem.php?pid=1060) 





Accepted Code

```java
package cn.edu.hdu.acm;

import java.math.BigInteger;
import java.util.Scanner;

public class Main1047 {

    public static void main(String[] args) {
        Scanner scn = new Scanner(System.in);
        int casesNumber = scn.nextInt();
        for (int cases = 1; cases <= casesNumber; ++cases) {
            if (1 != cases) {
                System.out.println();
            }
            BigInteger result = BigInteger.ZERO;
            while (scn.hasNext()) {
                BigInteger number = scn.nextBigInteger();
                if (number.equals(BigInteger.ZERO)) {
                    break;
                }
                result = result.add(number);
            }
            System.out.println(result);
        }
        scn.close();
    }
}

```

