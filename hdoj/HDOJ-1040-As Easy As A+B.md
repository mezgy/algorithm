# As Easy As A+B

**Time Limit: 2000/1000 MS (Java/Others)    Memory Limit: 65536/32768 K (Java/Others)Total Submission(s): 83360    Accepted Submission(s): 35318**

Problem Description

These days, I am thinking about a question, how can I get a problem as easy as A+B? It is fairly difficulty to do such a thing. Of course, I got it after many waking nights.
Give you some integers, your task is to sort these number ascending (升序).
You should know how easy the problem is now!
Good luck!

 



Input

Input contains multiple test cases. The first line of the input is a single integer T which is the number of test cases. T test cases follow. Each test case contains an integer N (1<=N<=1000 the number of integers to be sorted) and then N integers follow in the same line.
It is guarantied that all integers are in the range of 32-int.

 



Output

For each case, print the sorting result, and one line one case.

 



Sample Input

```
2
3 2 1 3
9 1 4 7 2 5 8 3 6 9
```

 



Sample Output

```
1 2 3
1 2 3 4 5 6 7 8 9
```

 



Author

lcy

 



Recommend

We have carefully selected several similar problems for you:  [1096](http://acm.hdu.edu.cn/showproblem.php?pid=1096) [1090](http://acm.hdu.edu.cn/showproblem.php?pid=1090) [1091](http://acm.hdu.edu.cn/showproblem.php?pid=1091) [1093](http://acm.hdu.edu.cn/showproblem.php?pid=1093) [1089](http://acm.hdu.edu.cn/showproblem.php?pid=1089) 





Accepted Code

```java
package cn.edu.hdu.acm;

import java.util.Arrays;
import java.util.Scanner;

public class Main1040{

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int n = sc.nextInt();
        while(n-->0){
            int num = sc.nextInt();
            int a [] = new int [num];
            for(int i=0;i<a.length;i++){
                a[i] = sc.nextInt();
            }
            Arrays.sort(a);
            for(int i:a){
                if(i!=a[a.length-1]){
                    System.out.print(i+" ");
                }
            }
            System.out.println(a[a.length-1]);
        }
    }
}
```

