# Robot Motion

**Time Limit: 2000/1000 MS (Java/Others)    Memory Limit: 65536/32768 K (Java/Others)Total Submission(s): 15747    Accepted Submission(s): 7281**

Problem Description

![img](http://acm.hdu.edu.cn/data/images/1035-1.gif)

A robot has been programmed to follow the instructions in its path. Instructions for the next direction the robot is to move are laid down in a grid. The possible instructions are

N north (up the page)
S south (down the page)
E east (to the right on the page)
W west (to the left on the page)

For example, suppose the robot starts on the north (top) side of Grid 1 and starts south (down). The path the robot follows is shown. The robot goes through 10 instructions in the grid before leaving the grid.

Compare what happens in Grid 2: the robot goes through 3 instructions only once, and then starts a loop through 8 instructions, and never exits.

You are to write a program that determines how long it takes a robot to get out of the grid or how the robot loops around.

 



Input

There will be one or more grids for robots to navigate. The data for each is in the following form. On the first line are three integers separated by blanks: the number of rows in the grid, the number of columns in the grid, and the number of the column in which the robot enters from the north. The possible entry columns are numbered starting with one at the left. Then come the rows of the direction instructions. Each grid will have at least one and at most 10 rows and columns of instructions. The lines of instructions contain only the characters N, S, E, or W with no blanks. The end of input is indicated by a row containing 0 0 0.

 



Output

For each grid in the input there is one line of output. Either the robot follows a certain number of instructions and exits the grid on any one the four sides or else the robot follows the instructions on a certain number of locations once, and then the instructions on some number of locations repeatedly. The sample input below corresponds to the two grids above and illustrates the two forms of output. The word "step" is always immediately followed by "(s)" whether or not the number before it is 1.

 



Sample Input

```
3 6 5
NEESWE
WWWESS
SNWWWW
4 5 1
SESWE
EESNW
NWEEN
EWSEN
0 0 
```

 



Sample Output

```
10 step(s) to exit
3 step(s) before a loop of 8 step(s)
```

 



Source

[Mid-Central USA 1999](http://acm.hdu.edu.cn/search.php?field=problem&key=Mid-Central+USA+1999&source=1&searchmode=source)

 



Recommend

We have carefully selected several similar problems for you:  [2553](http://acm.hdu.edu.cn/showproblem.php?pid=2553) [1258](http://acm.hdu.edu.cn/showproblem.php?pid=1258) [1045](http://acm.hdu.edu.cn/showproblem.php?pid=1045) [2660](http://acm.hdu.edu.cn/showproblem.php?pid=2660) [1312](http://acm.hdu.edu.cn/showproblem.php?pid=1312) 

 



Accepted  Code

```java
package cn.edu.hdu.acm;

import java.util.Scanner;

public class Main1035 {

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        while(sc.hasNext()){
            int n = sc.nextInt();
            int m = sc.nextInt();
            int s = sc.nextInt();
            if (n==0&&m==0&&s==0) {
                break;
            }
            String strs[] = new String[n];
            for (int i = 0; i < strs.length; i++) {
                strs[i] = sc.next();
            }
            int step[][] = new int[n][m];
            boolean isExit = true;
            int x = s-1;
            int y = 0;
            int i = 1;
            step[y][x] = i;
            while(true){
                char c = strs[y].charAt(x);
                if (c=='W') {
                    x--;
                }
                if (c=='E') {
                    x++;
                }
                if (c=='N') {
                    y--;
                }
                if (c=='S') {
                    y++;
                }
                if (x<0||x>=m||y<0||y>=n) {//走出去了
                    break;
                }
                if (step[y][x]!=0) {//开始循环
                    isExit = false;
                    break;
                }
                i++;
                step[y][x]= i;
            }
            if (isExit) {
                System.out.println(i+" step(s) to exit");
            }else{
                System.out.println(step[y][x]-1+" step(s) before a loop of "+(i-step[y][x]+1)+" step(s)");
            }
        }
        sc.close();
    }
}

```

