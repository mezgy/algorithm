# Gridland

**Time Limit: 2000/1000 MS (Java/Others)    Memory Limit: 65536/32768 K (Java/Others)Total Submission(s): 7420    Accepted Submission(s): 3406**

Problem Description

For years, computer scientists have been trying to find efficient solutions to different computing problems. For some of them efficient algorithms are already available, these are the “easy” problems like sorting, evaluating a polynomial or finding the shortest path in a graph. For the “hard” ones only exponential-time algorithms are known. The traveling-salesman problem belongs to this latter group. Given a set of N towns and roads between these towns, the problem is to compute the shortest path allowing a salesman to visit each of the towns once and only once and return to the starting point.

The president of Gridland has hired you to design a program that calculates the length of the shortest traveling-salesman tour for the towns in the country. In Gridland, there is one town at each of the points of a rectangular grid. Roads run from every town in the directions North, Northwest, West, Southwest, South, Southeast, East, and Northeast, provided that there is a neighbouring town in that direction. The distance between neighbouring towns in directions North–South or East–West is 1 unit. The length of the roads is measured by the Euclidean distance. For example, Figure 7 shows 2 × 3-Gridland, i.e., a rectangular grid of dimensions 2 by 3. In 2 × 3-Gridland, the shortest tour has length 6.

![img](http://acm.hdu.edu.cn/data/images/1046-1.jpg)

 



Input

The first line contains the number of scenarios.

For each scenario, the grid dimensions m and n will be given as two integer numbers in a single line, separated by a single blank, satisfying 1 < m < 50 and 1 < n < 50.

 



Output

The output for each scenario begins with a line containing “Scenario #i:”, where i is the number of the scenario starting at 1. In the next line, print the length of the shortest traveling-salesman tour rounded to two decimal digits. The output for every scenario ends with a blank line.

 



Sample Input

```
2
2 2
2 3
```

 



Sample Output

```
Scenario #1:
4.00

Scenario #2:
6.00
```

 



Source

[Northwestern Europe 2001](http://acm.hdu.edu.cn/search.php?field=problem&key=Northwestern+Europe+2001&source=1&searchmode=source)

 



Recommend

We have carefully selected several similar problems for you:  [1124](http://acm.hdu.edu.cn/showproblem.php?pid=1124) [1129](http://acm.hdu.edu.cn/showproblem.php?pid=1129) [1084](http://acm.hdu.edu.cn/showproblem.php?pid=1084) [1049](http://acm.hdu.edu.cn/showproblem.php?pid=1049) [1073](http://acm.hdu.edu.cn/showproblem.php?pid=1073) 





Accepted Code

```java
//此题演示错误没有AC，我感觉没问题，可能是格式错了
package cn.edu.hdu.acm;

import java.util.Scanner;

public class Main1046 {

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        int t = scanner.nextInt();
        int c = 1;
        double result=0;
        while (t-- > 0) {
            int n = scanner.nextInt();
            int m = scanner.nextInt();
            if (n % 2 == 0 || m % 2 == 0) {
                result = m*n;
            } else {
                result = m*n+0.41;
            }
            System.out.println("Scenario #" + c++ + ":");
            System.out.printf("%.2f", result);
            if (t!=0) {
                System.out.println("\n");
            }
        }
    }
}
```

