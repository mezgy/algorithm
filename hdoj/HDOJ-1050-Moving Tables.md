# Moving Tables

**Time Limit: 2000/1000 MS (Java/Others)    Memory Limit: 65536/32768 K (Java/Others)Total Submission(s): 47523    Accepted Submission(s): 15421**

Problem Description

The famous ACM (Advanced Computer Maker) Company has rented a floor of a building whose shape is in the following figure.

![img](http://acm.hdu.edu.cn/data/images/1050-1.gif)

The floor has 200 rooms each on the north side and south side along the corridor. Recently the Company made a plan to reform its system. The reform includes moving a lot of tables between rooms. Because the corridor is narrow and all the tables are big, only one table can pass through the corridor. Some plan is needed to make the moving efficient. The manager figured out the following plan: Moving a table from a room to another room can be done within 10 minutes. When moving a table from room i to room j, the part of the corridor between the front of room i and the front of room j is used. So, during each 10 minutes, several moving between two rooms not sharing the same part of the corridor will be done simultaneously. To make it clear the manager illustrated the possible cases and impossible cases of simultaneous moving.

![img](http://acm.hdu.edu.cn/data/images/1050-2.gif)

For each room, at most one table will be either moved in or moved out. Now, the manager seeks out a method to minimize the time to move all the tables. Your job is to write a program to solve the manager’s problem.

 



Input

The input consists of T test cases. The number of test cases ) (T is given in the first line of the input. Each test case begins with a line containing an integer N , 1<=N<=200 , that represents the number of tables to move. Each of the following N lines contains two positive integers s and t, representing that a table is to move from room number s to room number t (each room number appears at most once in the N lines). From the N+3-rd line, the remaining test cases are listed in the same manner as above.

 



Output

The output should contain the minimum time in minutes to complete the moving, one per line.

 



Sample Input

```
3 
4 
10 20 
30 40 
50 60 
70 80 
2 
1 3 
2 200 
3 
10 100 
20 80 
30 50 
```

 



Sample Output

```
10
20
30
```

 



Source

[Asia 2001, Taejon (South Korea)](http://acm.hdu.edu.cn/search.php?field=problem&key=Asia+2001%2C+Taejon+(South+Korea)&source=1&searchmode=source)

 



Recommend

We have carefully selected several similar problems for you:  [2037](http://acm.hdu.edu.cn/showproblem.php?pid=2037) [1051](http://acm.hdu.edu.cn/showproblem.php?pid=1051) [1052](http://acm.hdu.edu.cn/showproblem.php?pid=1052) [1789](http://acm.hdu.edu.cn/showproblem.php?pid=1789) [1053](http://acm.hdu.edu.cn/showproblem.php?pid=1053) 





Accepted Code

```java
//经典贪心
package cn.edu.hdu.acm;

import java.util.Arrays;
import java.util.Scanner;

public class Main1050 {

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int t = sc.nextInt();
        while((t--)!=0){
            int n = sc.nextInt();
            int[] cout = new int[401];
            while((n--)!=0){
                int s = sc.nextInt();
                int e = sc.nextInt();
                int l = Math.min(s, e);
                int r = Math.max(s, e);
                if(l%2==0) {
                    l--;
                }
                if(r%2==1) {
                    r++;
                }
                for (int i = l; i <= r; i++) {
                    cout[i] += 10;
                }
            }
            Arrays.sort(cout);
            System.out.println(cout[cout.length-1]);
        }
    }
}

```

