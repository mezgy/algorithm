# A + B Problem II

**Time Limit: 2000/1000 MS (Java/Others)    Memory Limit: 65536/32768 K (Java/Others)Total Submission(s): 488978    Accepted Submission(s): 94379**

Problem Description

I have a very simple problem for you. Given two integers A and B, your job is to calculate the Sum of A + B.

 



Input

The first line of the input contains an integer T(1<=T<=20) which means the number of test cases. Then T lines follow, each line consists of two positive integers, A and B. Notice that the integers are very large, that means you should not process them by using 32-bit integer. You may assume the length of each integer will not exceed 1000.

 



Output

For each test case, you should output two lines. The first line is "Case #:", # means the number of the test case. The second line is the an equation "A + B = Sum", Sum means the result of A + B. Note there are some spaces int the equation. Output a blank line between two test cases.

 



Sample Input

```
2
1 2
112233445566778899 998877665544332211
```

 



Sample Output

```
Case 1:
1 + 2 = 3

Case 2:
112233445566778899 + 998877665544332211 = 1111111111111111110
```

 



Author

Ignatius.L

 



Recommend

We have carefully selected several similar problems for you:  [1004](http://acm.hdu.edu.cn/showproblem.php?pid=1004) [1003](http://acm.hdu.edu.cn/showproblem.php?pid=1003) [1008](http://acm.hdu.edu.cn/showproblem.php?pid=1008) [1005](http://acm.hdu.edu.cn/showproblem.php?pid=1005) [1089](http://acm.hdu.edu.cn/showproblem.php?pid=1089) 





Accepted Code

```java
package cn.edu.hdu.acm;

import java.math.BigInteger;
import java.util.Scanner;

public class Main1002 {
    public static void main(String[] args) {
        Scanner cin=new Scanner(System.in);
        int n= cin.nextInt();
        int index=1;
        while(n-->0){
            String s1=cin.next();
            String s2=cin.next();
            BigInteger a=new BigInteger(s1); 
            BigInteger b= new BigInteger(s2);
            BigInteger c= a.add(b);
            System.out.println("Case " + (index++) + ":");
            System.out.println(a.toString()+" + "+b.toString()+" = "+c.toString());
            if(n>0)
                System.out.println("");
        }
        cin.close();
    }
 
}

```

