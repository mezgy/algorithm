# Ignatius and the Princess IV

**Time Limit: 2000/1000 MS (Java/Others)    Memory Limit: 65536/32767 K (Java/Others)Total Submission(s): 52139    Accepted Submission(s): 23519**

Problem Description

"OK, you are not too bad, em... But you can never pass the next test." feng5166 says.

"I will tell you an odd number N, and then N integers. There will be a special integer among them, you have to tell me which integer is the special one after I tell you all the integers." feng5166 says.

"But what is the characteristic of the special integer?" Ignatius asks.

"The integer will appear at least (N+1)/2 times. If you can't find the right integer, I will kill the Princess, and you will be my dinner, too. Hahahaha....." feng5166 says.

Can you find the special integer for Ignatius?

 



Input

The input contains several test cases. Each test case contains two lines. The first line consists of an odd integer N(1<=N<=999999) which indicate the number of the integers feng5166 will tell our hero. The second line contains the N integers. The input is terminated by the end of file.

 



Output

For each test case, you have to output only one line which contains the special number you have found.

 



Sample Input

```
5
1 3 2 3 3
11
1 1 1 1 1 5 5 5 5 5 5
7
1 1 1 1 1 1 1
```

 



Sample Output

```
3
5
1
```

 



Author

Ignatius.L

 



Recommend

We have carefully selected several similar problems for you:  [1040](http://acm.hdu.edu.cn/showproblem.php?pid=1040) [1074](http://acm.hdu.edu.cn/showproblem.php?pid=1074) [1171](http://acm.hdu.edu.cn/showproblem.php?pid=1171) [1203](http://acm.hdu.edu.cn/showproblem.php?pid=1203) [1087](http://acm.hdu.edu.cn/showproblem.php?pid=1087) 





Accepted Code

```java
package cn.edu.hdu.acm;

import java.util.Scanner;

public class Main1029 {
    static int a[] = new int[10000];
    private static int n;
    private static int x;
    private static boolean bo;

    public static void main(String[] args) {

        Scanner sc = new Scanner(System.in);
        while (sc.hasNext()) {
            n = sc.nextInt();
            int k = (n + 1) / 2;
            int flag = 0;
            bo = false;
            a=new int[10000]; 
            for (int i = 0; i < n; i++) {
                x = sc.nextInt();
                a[x]++;
                if (a[x] >= k) {
                    flag = x;
                    bo = true;
                }   

            }
            System.out.println(flag);

        }

    }
}

```

