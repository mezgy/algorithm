# Big Number

**Time Limit: 2000/1000 MS (Java/Others)    Memory Limit: 65536/32768 K (Java/Others)Total Submission(s): 47754    Accepted Submission(s): 23556**

Problem Description

In many applications very large integers numbers are required. Some of these applications are using keys for secure transmission of data, encryption, etc. In this problem you are given a number, you have to determine the number of digits in the factorial of the number.

 



Input

Input consists of several lines of integer numbers. The first line contains an integer n, which is the number of cases to be tested, followed by n lines, one integer 1 ≤ n ≤ 107 on each line.

 



Output

The output contains the number of digits in the factorial of the integers appearing in the input.

 



Sample Input

```
2
10
20
```

 



Sample Output

```
7
19
```

 



Source

[Asia 2002, Dhaka (Bengal)](http://acm.hdu.edu.cn/search.php?field=problem&key=Asia+2002%2C+Dhaka+(Bengal)&source=1&searchmode=source)

 



Recommend

JGShining   |   We have carefully selected several similar problems for you:  [1071](http://acm.hdu.edu.cn/showproblem.php?pid=1071) [1019](http://acm.hdu.edu.cn/showproblem.php?pid=1019) [1021](http://acm.hdu.edu.cn/showproblem.php?pid=1021) [1020](http://acm.hdu.edu.cn/showproblem.php?pid=1020) [1061](http://acm.hdu.edu.cn/showproblem.php?pid=1061) 





Accepted Code

```java
//题目大意：问你n!有多少位。
//解题思路：最先想到的就是对10求余，n!=1*2*3*4*……*n 不过也可以使用斯特林公式直接求解。斯特林公式：n!  约等于 sqrt(2*PI*n)*(n/e)^n.

/*直接一位一位求*/
package cn.edu.hdu.acm;

import java.util.Scanner;
 
public class Main1018 {

    public static void main(String args[]) {
    	 Scanner cin = new Scanner(System.in);
         int tes,i,p,j;
         tes=cin.nextInt();
         for(i=0;i<tes;i++) {
        	 p=cin.nextInt();
        	 double sum=0;
        	 for(j=1;j<=p;j++)
        	 	 sum+=Math.log((double)j)/Math.log(10.0);
        	 int res=(int)sum+1;
             System.out.println(res);
         }
    }
}

/*使用斯特林公式*/
package cn.edu.hdu.acm;

import java.util.Scanner;
 
public class Main1018 {
    
	public static void main(String args[]) {
    	 Scanner cin = new Scanner(System.in);
         int tes,i,p,j;
         tes=cin.nextInt();
         double PI=Math.acos(-1.0);
         double e=Math.E;
         for(i=0;i<tes;i++) {
        	 p=cin.nextInt();
        	 double res1=1.0/2.0*Math.log(2.0*PI*p)/Math.log(10.0)+p*Math.log(p/e)/Math.log(10.0);
        	 int res=(int)res1+1;
             System.out.println(res);
         }
    }
}
```



 