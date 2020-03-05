# Train Problem II

**Time Limit: 2000/1000 MS (Java/Others)    Memory Limit: 65536/32768 K (Java/Others)Total Submission(s): 12642    Accepted Submission(s): 6752**

Problem Description

As we all know the Train Problem I, the boss of the Ignatius Train Station want to know if all the trains come in strict-increasing order, how many orders that all the trains can get out of the railway.

 



Input

The input contains several test cases. Each test cases consists of a number N(1<=N<=100). The input is terminated by the end of file.

 



Output

For each test case, you should output how many ways that all the trains can get out of the railway.

 



Sample Input

```
1
2
3
10
```

 



Sample Output

```
1
2
5
16796

Hint
The result will be very large, so you may not process it by 32-bit integers.
 
```

 



Author

Ignatius.L

 



Recommend

We have carefully selected several similar problems for you:  [1133](http://acm.hdu.edu.cn/showproblem.php?pid=1133) [1130](http://acm.hdu.edu.cn/showproblem.php?pid=1130) [1131](http://acm.hdu.edu.cn/showproblem.php?pid=1131) [1134](http://acm.hdu.edu.cn/showproblem.php?pid=1134) [2067](http://acm.hdu.edu.cn/showproblem.php?pid=2067) 





Accepted Code

```java
package cn.edu.hdu.acm;

import java.math.BigInteger;
import java.util.*;

public class Main1023 {
	
public static void main(String[] args){
    Scanner input = new Scanner(System.in);
    BigInteger a=new BigInteger("1");
    BigInteger b=new BigInteger("2");
    BigInteger c=new BigInteger("4");
    BigInteger d=new BigInteger("1");
    BigInteger ans[]=new BigInteger[105];
    ans[1]=a;
    for(int i=2;i<=100;i++){
        d=d.add(a);
        ans[i]=ans[i-1].multiply(c.multiply(d).subtract(b)).divide(d.add(a));
    	}
    while(input.hasNext()){
    int t=input.nextInt();
    System.out.println(ans[t]);
    	}
    }
}

```

