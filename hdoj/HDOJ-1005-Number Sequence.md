# Number Sequence

**Time Limit: 2000/1000 MS (Java/Others)    Memory Limit: 65536/32768 K (Java/Others)Total Submission(s): 225316    Accepted Submission(s): 57178**

Problem Description

A number sequence is defined as follows:

f(1) = 1, f(2) = 1, f(n) = (A * f(n - 1) + B * f(n - 2)) mod 7.

Given A, B, and n, you are to calculate the value of f(n).

 



Input

The input consists of multiple test cases. Each test case contains 3 integers A, B and n on a single line (1 <= A, B <= 1000, 1 <= n <= 100,000,000). Three zeros signal the end of input and this test case is not to be processed.

 



Output

For each test case, print the value of f(n) on a single line.

 



Sample Input

```
1 1 3
1 2 10
0 0 0
```

 



Sample Output

```
2
5
```

 



Author

CHEN, Shunbao

 



Source

[ZJCPC2004](http://acm.hdu.edu.cn/search.php?field=problem&key=ZJCPC2004&source=1&searchmode=source)

 



Recommend

JGShining   |   We have carefully selected several similar problems for you:  [1008](http://acm.hdu.edu.cn/showproblem.php?pid=1008) [1021](http://acm.hdu.edu.cn/showproblem.php?pid=1021) [1019](http://acm.hdu.edu.cn/showproblem.php?pid=1019) [1009](http://acm.hdu.edu.cn/showproblem.php?pid=1009) [1012](http://acm.hdu.edu.cn/showproblem.php?pid=1012) 





Accepted Code

``` java
package cn.edu.hdu.acm;

import java.util.*;

public class Main1005{

    public static void main(String[] args) throws Exception{
        Scanner cin = new Scanner(System.in);
        int a = cin.nextInt();
        int b = cin.nextInt();
        int n = cin.nextInt();

        while(a != 0 && b != 0 && n != 0 ){
            System.out.println(fun(a,b,n%48));
            a = cin.nextInt();
            b = cin.nextInt();
            n = cin.nextInt();
        }

    }
    public static int fun(int a,int b,int n){
        return (n == 1 || n == 2) ? 1 :(a*fun(a,b,n-1) + b*fun(a,b,n-2))%7;
    }
}
```

