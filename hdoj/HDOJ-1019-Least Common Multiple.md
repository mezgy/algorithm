# Least Common Multiple

**Time Limit: 2000/1000 MS (Java/Others)    Memory Limit: 65536/32768 K (Java/Others)Total Submission(s): 69221    Accepted Submission(s): 26511**

Problem Description

The least common multiple (LCM) of a set of positive integers is the smallest positive integer which is divisible by all the numbers in the set. For example, the LCM of 5, 7 and 15 is 105.



 



Input

Input will consist of multiple problem instances. The first line of the input will contain a single integer indicating the number of problem instances. Each instance will consist of a single line of the form m n1 n2 n3 ... nm where m is the number of integers in the set and n1 ... nm are the integers. All integers will be positive and lie within the range of a 32-bit integer.

 



Output

For each problem instance, output a single line containing the corresponding LCM. All results will lie in the range of a 32-bit integer.

 



Sample Input

```
2
3 5 7 15
6 4 10296 936 1287 792 1
```

 



Sample Output

```
105
10296
```

 



Source

[East Central North America 2003, Practice](http://acm.hdu.edu.cn/search.php?field=problem&key=East+Central+North+America+2003%2C+Practice&source=1&searchmode=source)

 



Recommend

JGShining   |   We have carefully selected several similar problems for you:  [1021](http://acm.hdu.edu.cn/showproblem.php?pid=1021) [1061](http://acm.hdu.edu.cn/showproblem.php?pid=1061) [1049](http://acm.hdu.edu.cn/showproblem.php?pid=1049) [1108](http://acm.hdu.edu.cn/showproblem.php?pid=1108) [1020](http://acm.hdu.edu.cn/showproblem.php?pid=1020) 





Accepted Code

```java
package cn.edu.hdu.acm;

import java.util.Scanner;

public class Main1019 {
 
    int gcd(int a,int b){
        if(b==0) return a;
        else return gcd(b,a%b);
    }
    int lcm(int a,int b){
        long tmp=(long)a*b;
        int x=gcd(a,b);
        tmp/=x;
        return (int)tmp;
    }
    
    public static void main(String[] args) {
        int t;
        Scanner cin=new Scanner(System.in);
        t=cin.nextInt();
        Main1019 mObj=new Main1019();
        while(t!=0){
            --t;
            int m=cin.nextInt();
            int ans=cin.nextInt();
            int b;
            for(int i=1;i<m;++i){
                b=cin.nextInt();
                ans=mObj.lcm(ans, b);
            }
            System.out.println(ans);
        }
        cin.close();
    }
}

```

