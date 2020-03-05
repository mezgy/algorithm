# Tick and Tick

**Time Limit: 2000/1000 MS (Java/Others)    Memory Limit: 65536/32768 K (Java/Others)Total Submission(s): 25009    Accepted Submission(s): 6865**

Problem Description

The three hands of the clock are rotating every second and meeting each other many times everyday. Finally, they get bored of this and each of them would like to stay away from the other two. A hand is happy if it is at least D degrees from any of the rest. You are to calculate how much time in a day that all the hands are happy.

 



Input

The input contains many test cases. Each of them has a single line with a real number D between 0 and 120, inclusively. The input is terminated with a D of -1.

 



Output

For each D, print in a single line the percentage of time in a day that all of the hands are happy, accurate up to 3 decimal places.

 



Sample Input

```
0
120
90
-1
```

 



Sample Output

```
100.000
0.000
6.251
```

 



Author

PAN, Minghao

 



Source

[ZJCPC2004](http://acm.hdu.edu.cn/search.php?field=problem&key=ZJCPC2004&source=1&searchmode=source)

 



Recommend

JGShining   |   We have carefully selected several similar problems for you:  [1007](http://acm.hdu.edu.cn/showproblem.php?pid=1007) [1008](http://acm.hdu.edu.cn/showproblem.php?pid=1008) [1010](http://acm.hdu.edu.cn/showproblem.php?pid=1010) [1009](http://acm.hdu.edu.cn/showproblem.php?pid=1009) [1011](http://acm.hdu.edu.cn/showproblem.php?pid=1011) 





Accepted Code

```java
package cn.edu.hdu.acm;

import java.util.Scanner;

public class Main1006 {

public static void main(String args[]){
    Scanner s=new Scanner(System.in);
    while(true){
        double D=s.nextDouble(); 
        if(D==-1)
            break;

        double mhmin[]=new double[11];
        //这里存储的不是角度，而是时间
        double mhmax[]=new double[11];
        for(int i=0;i<11;i++) { 
        //360*i+D为俩指针之间最小相差角度，相差一度需要的时间为120/11，所以*120/11转换为相差这么多度需要的时间。
        	mhmin[i]=(360*i+D)*120/11;
            mhmax[i]=(360*i+360-D)*120/11;
        }
        double smmin[]=new double[708];
        double smmax[]=new double[708];
        for(int i=0;i<708;i++){
            smmin[i]=(360*i+D)/5.9;
            smmax[i]=(360*i+360-D)/5.9;
        }
        double shmin[]=new double[719];
        double shmax[]=new double[719];
        for(int i=0;i<719;i++){
            shmin[i]=(360*i+D)*120/719;
            shmax[i]=(360*i+360-D)*120/719;
        }
        double countTime=0;
        for(int i=0;i<11;i++){
            for(int j=0;j<708;j++){
                if(smmin[j]<mhmax[i]&&smmax[j]>mhmin[i]){
                    for(int k=0;k<719;k++){
                        if(shmin[k]<smmax[j]&&shmax[k]>smmin[j]){
                            if(shmin[k]<mhmax[i]&&shmax[k]>mhmin[i]){
                                double min=Max(shmin[k],smmin[j],mhmin[i]);
                                double max=Min(shmax[k],smmax[j],mhmax[i]);
                                countTime=countTime+max-min;
                            }
                        }
                    }
                }
            }
        }
        double percent=countTime/432;
        System.out.printf("%.3f", percent);
        System.out.println();
	}
}

private static double Min(double d, double e, double f) {
    double min=0;
    min=d>e?e:d;
    min=min>f?f:min;
    return min;
	}

private static double Max(double d, double e, double f) {
    double max=0;
    max=d>e?d:e;
    max=max>f?max:f;
    return max;
	}
}
```

