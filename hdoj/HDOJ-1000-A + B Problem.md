# A + B Problem

**Time Limit: 2000/1000 MS (Java/Others)    Memory Limit: 65536/32768 K (Java/Others)Total Submission(s): 888827    Accepted Submission(s): 267559**

Problem Description

Calculate *A + B*.

 



Input

Each line will contain two integers *A* and *B*. Process to end of file.

 



Output

For each case, output *A + B* in one line.

 



Sample Input

```
1 1
```

 



Sample Output

```
2
```

 



Author

HDOJ

 



Recommend

We have carefully selected several similar problems for you:  [1089](http://acm.hdu.edu.cn/showproblem.php?pid=1089) [1002](http://acm.hdu.edu.cn/showproblem.php?pid=1002) [1090](http://acm.hdu.edu.cn/showproblem.php?pid=1090) [1091](http://acm.hdu.edu.cn/showproblem.php?pid=1091) [1092](http://acm.hdu.edu.cn/showproblem.php?pid=1092) 





Accepted Code

``` java
package cn.edu.hdu.acm;

import java.util.*;

public class Main1000 {
	public static void main(String[] args){
        Scanner in = new Scanner(System.in);
        while(in.hasNextInt())
        {
            int a = in.nextInt();
            int b = in.nextInt();
            System.out.println(a+b);
        }
    }
}
```

