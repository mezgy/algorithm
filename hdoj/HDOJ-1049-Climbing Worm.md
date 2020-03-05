# Climbing Worm

**Time Limit: 2000/1000 MS (Java/Others)    Memory Limit: 65536/32768 K (Java/Others)Total Submission(s): 25333    Accepted Submission(s): 17227**

Problem Description

An inch worm is at the bottom of a well n inches deep. It has enough energy to climb u inches every minute, but then has to rest a minute before climbing again. During the rest, it slips down d inches. The process of climbing and resting then repeats. How long before the worm climbs out of the well? We'll always count a portion of a minute as a whole minute and if the worm just reaches the top of the well at the end of its climbing, we'll assume the worm makes it out.

 



Input

There will be multiple problem instances. Each line will contain 3 positive integers n, u and d. These give the values mentioned in the paragraph above. Furthermore, you may assume d < u and n < 100. A value of n = 0 indicates end of output.

 



Output

Each input instance should generate a single integer on a line, indicating the number of minutes it takes for the worm to climb out of the well.

 



Sample Input

```
10 2 1
20 3 1
0 0 0
```

 



Sample Output

```
17
19
```

 



Source

[East Central North America 2002](http://acm.hdu.edu.cn/search.php?field=problem&key=East+Central+North+America+2002&source=1&searchmode=source)

 



Recommend

We have carefully selected several similar problems for you:  [1108](http://acm.hdu.edu.cn/showproblem.php?pid=1108) [1071](http://acm.hdu.edu.cn/showproblem.php?pid=1071) [1061](http://acm.hdu.edu.cn/showproblem.php?pid=1061) [1170](http://acm.hdu.edu.cn/showproblem.php?pid=1170) [2035](http://acm.hdu.edu.cn/showproblem.php?pid=2035) 





Accepted Code

```java
//模拟水题
package cn.edu.hdu.acm;

import java.util.Scanner;

public class Main1049 {

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        while (scanner.hasNext()){
            int restult=0,n,u,d;
            n = scanner.nextInt();
            u = scanner.nextInt();
            d = scanner.nextInt();
            if (n == 0) {
                break;
            }
            while(true){
                n = n-u;
                restult++;
                if (n<=0){
                    System.out.println(restult);
                    break;
                }else {
                    n=n+d;
                    restult++;
                }
            }
        }
    }
}

```

