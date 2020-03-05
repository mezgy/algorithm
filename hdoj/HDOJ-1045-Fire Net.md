# Fire Net

**Time Limit: 2000/1000 MS (Java/Others)    Memory Limit: 65536/32768 K (Java/Others)Total Submission(s): 17848    Accepted Submission(s): 10873**

Problem Description

Suppose that we have a square city with straight streets. A map of a city is a square board with n rows and n columns, each representing a street or a piece of wall.

A blockhouse is a small castle that has four openings through which to shoot. The four openings are facing North, East, South, and West, respectively. There will be one machine gun shooting through each opening.

Here we assume that a bullet is so powerful that it can run across any distance and destroy a blockhouse on its way. On the other hand, a wall is so strongly built that can stop the bullets.

The goal is to place as many blockhouses in a city as possible so that no two can destroy each other. A configuration of blockhouses is legal provided that no two blockhouses are on the same horizontal row or vertical column in a map unless there is at least one wall separating them. In this problem we will consider small square cities (at most 4x4) that contain walls through which bullets cannot run through.

The following image shows five pictures of the same board. The first picture is the empty board, the second and third pictures show legal configurations, and the fourth and fifth pictures show illegal configurations. For this board, the maximum number of blockhouses in a legal configuration is 5; the second picture shows one way to do it, but there are several other ways.

![img](http://acm.hdu.edu.cn/data/images/1045-1.jpg)

Your task is to write a program that, given a description of a map, calculates the maximum number of blockhouses that can be placed in the city in a legal configuration.

 



Input

The input file contains one or more map descriptions, followed by a line containing the number 0 that signals the end of the file. Each map description begins with a line containing a positive integer n that is the size of the city; n will be at most 4. The next n lines each describe one row of the map, with a '.' indicating an open space and an uppercase 'X' indicating a wall. There are no spaces in the input file.

 



Output

For each test case, output one line containing the maximum number of blockhouses that can be placed in the city in a legal configuration.

 



Sample Input

```
4
.X..
....
XX..
....
2
XX
.X
3
.X.
X.X
.X.
3
...
.XX
.XX
4
....
....
....
....
0
```

 



Sample Output

```
5
1
5
2
4
```

 



Source

[Zhejiang University Local Contest 2001](http://acm.hdu.edu.cn/search.php?field=problem&key=Zhejiang+University+Local+Contest+2001&source=1&searchmode=source)

 



Recommend

We have carefully selected several similar problems for you:  [1051](http://acm.hdu.edu.cn/showproblem.php?pid=1051) [1050](http://acm.hdu.edu.cn/showproblem.php?pid=1050) [1175](http://acm.hdu.edu.cn/showproblem.php?pid=1175) [1241](http://acm.hdu.edu.cn/showproblem.php?pid=1241) [1312](http://acm.hdu.edu.cn/showproblem.php?pid=1312) 





Accepted Code

```java
package cn.edu.hdu.acm;

import java.io.BufferedInputStream;
import java.util.Scanner;

public class Main1045 {
    static char maze[][];
    static int max, result, N;

    public static boolean placeable(int i, int j) {
        if (maze[i][j] == 'X') {
            return false;
        }
        int k=j;
        while (k >= 0 && maze[i][k] != 'X') {
            if (maze[i][k--] == '*') {
                return false;
            }
        }
        k=i;
        while (k >= 0 && maze[k][j] != 'X') {
            if (maze[k--][j] == '*') {
                return false;
            }
        }
        return true;
    }

    public static void DFS(int i, int j, int max) {
        if ((i==N-1&&j==N)||(i==N&&j==N-1)) {
            result = max > result ? max : result;
            return;
        } else if (i < N && j < N && placeable(i, j)) {
            maze[i][j] = '*';
            if (j == N - 1) {
                DFS(i + 1, 0, max + 1);
            } else {
                DFS(i, j + 1, max + 1);
            }
            maze[i][j] = '.';
        }
        if (j == N - 1) {
            DFS(i + 1, 0, max);
        } else {
            DFS(i, j + 1, max);
        }
    }

    public static void main(String[] args) {
        Scanner cin = new Scanner(new BufferedInputStream(System.in));
        while (cin.hasNext()) {
            N = cin.nextInt();
            if (N == 0) {
                return;
            }
            max = 0;
            result = 0;
            maze = new char[N][N];
            String str;
            for (int i = 0; i < N; i++) {
                str = cin.next();
                for (int j = 0; j < N; j++) {
                    maze[i][j] = str.charAt(j);
                }
            }
            DFS(0, 0, 0);
            System.out.println(result);
        }
    }
}

```

