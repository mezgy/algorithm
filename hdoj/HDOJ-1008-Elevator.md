# Elevator

**Time Limit: 2000/1000 MS (Java/Others)    Memory Limit: 65536/32768 K (Java/Others)Total Submission(s): 95846    Accepted Submission(s): 52137**

Problem Description

The highest building in our city has only one elevator. A request list is made up with N positive numbers. The numbers denote at which floors the elevator will stop, in specified order. It costs 6 seconds to move the elevator up one floor, and 4 seconds to move down one floor. The elevator will stay for 5 seconds at each stop.

For a given request list, you are to compute the total time spent to fulfill the requests on the list. The elevator is on the 0th floor at the beginning and does not have to return to the ground floor when the requests are fulfilled.

 



Input

There are multiple test cases. Each case contains a positive integer N, followed by N positive numbers. All the numbers in the input are less than 100. A test case with N = 0 denotes the end of input. This test case is not to be processed.

 



Output

Print the total time on a single line for each test case. 

 



Sample Input

```
1 2
3 2 3 1
0
```

 



Sample Output

```
17
41
```

 



Author

ZHENG, Jianqiang

 



Source

[ZJCPC2004](http://acm.hdu.edu.cn/search.php?field=problem&key=ZJCPC2004&source=1&searchmode=source)

 



Recommend

JGShining   |   We have carefully selected several similar problems for you:  [1009](http://acm.hdu.edu.cn/showproblem.php?pid=1009) [1021](http://acm.hdu.edu.cn/showproblem.php?pid=1021) [1108](http://acm.hdu.edu.cn/showproblem.php?pid=1108) [1019](http://acm.hdu.edu.cn/showproblem.php?pid=1019) [1061](http://acm.hdu.edu.cn/showproblem.php?pid=1061) 





Accepted Code

```java
package cn.edu.hdu.acm;

import java.util.Scanner;  

public class Main1008 {  
    public static void main(String[] args) {  
        Scanner in = new Scanner(System.in);  
        while(in.hasNext()){  
            int n = in.nextInt();  
            int floor_begin=0;  
            int floor_end=0;  
            int total_time = 0;  
            if(n==0)  
                break;  
            for(int i=0;i<n;i++)  
            {  
                int floor = in.nextInt();  
                floor_end = floor;  
                if(floor_end>floor_begin)  
                {  
                    total_time += (floor_end-floor_begin)*6;  
                }  
                else  
                {  
                    total_time += (floor_begin-floor_end)*4;  
                }  
                floor_begin = floor_end;  
            }  
            total_time += n*5;  
            System.out.println(total_time);      
        }  
    }  
  
}  

```

