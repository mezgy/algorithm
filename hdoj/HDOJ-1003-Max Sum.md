# Max Sum

**Time Limit: 2000/1000 MS (Java/Others)    Memory Limit: 65536/32768 K (Java/Others)Total Submission(s): 332042    Accepted Submission(s): 79058**

Problem Description

Given a sequence a[1],a[2],a[3]......a[n], your job is to calculate the max sum of a sub-sequence. For example, given (6,-1,5,4,-7), the max sum in this sequence is 6 + (-1) + 5 + 4 = 14.

 



Input

The first line of the input contains an integer T(1<=T<=20) which means the number of test cases. Then T lines follow, each line starts with a number N(1<=N<=100000), then N integers followed(all the integers are between -1000 and 1000).

 



Output

For each test case, you should output two lines. The first line is "Case #:", # means the number of the test case. The second line contains three integers, the Max Sum in the sequence, the start position of the sub-sequence, the end position of the sub-sequence. If there are more than one result, output the first one. Output a blank line between two cases.

 



Sample Input

```
2
5 6 -1 5 4 -7
7 0 6 -1 1 -6 7 -5
```

 



Sample Output

```
Case 1:
14 1 4

Case 2:
7 1 6
```

 



Author

Ignatius.L

 



Recommend

We have carefully selected several similar problems for you:  [1176](http://acm.hdu.edu.cn/showproblem.php?pid=1176) [1087](http://acm.hdu.edu.cn/showproblem.php?pid=1087) [1069](http://acm.hdu.edu.cn/showproblem.php?pid=1069) [2084](http://acm.hdu.edu.cn/showproblem.php?pid=2084) [1058](http://acm.hdu.edu.cn/showproblem.php?pid=1058) 





Accepted Code

```java
package cn.edu.hdu.acm;

import java.util.*;

public class Main1003 { 
    public static void main(String[] args) {
        int T = 0 , i = 0, j = 0;
        Scanner cin = new Scanner(System.in);
        T = cin.nextInt();
        for(i=1;i<=T;i++) {
            int n = 0;
            int temp = -1001, ans = -1001, s = 0, e = 0, ss = 0, ee = 0;
            n = cin.nextInt();
            for(j=1;j<=n;j++) {
                int t = cin.nextInt();
                if(temp + t < t) {
                    temp = t;
                    s = e = j;
                }
                else {
                    temp += t;
                    e++;
                }
                if(ans < temp) {
                    ans = temp;
                    ss = s;
                    ee = e;
                }
            }
            System.out.println("Case " + i + ":");
            System.out.println(ans + " " + ss + " " + ee);
            if(i != T) {
                System.out.println();
            }
        }
    }
} 
```

