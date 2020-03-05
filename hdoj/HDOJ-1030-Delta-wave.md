# Delta-wave

**Time Limit: 2000/1000 MS (Java/Others)    Memory Limit: 65536/32768 K (Java/Others)Total Submission(s): 12080    Accepted Submission(s): 4931**

Problem Description

A triangle field is numbered with successive integers in the way shown on the picture below.

![img](http://acm.hdu.edu.cn/data/images/1030-1.jpg)

The traveller needs to go from the cell with number M to the cell with number N. The traveller is able to enter the cell through cell edges only, he can not travel from cell to cell through vertices. The number of edges the traveller passes makes the length of the traveller's route.

Write the program to determine the length of the shortest route connecting cells with numbers N and M.

 



Input

Input contains two integer numbers M and N in the range from 1 to 1000000000 separated with space(s).

 



Output

Output should contain the length of the shortest route.

 



Sample Input

```
6 12 
```

 



Sample Output

```
3
```

 



Source

[Ural Collegiate Programming Contest 1998](http://acm.hdu.edu.cn/search.php?field=problem&key=Ural+Collegiate+Programming+Contest+1998&source=1&searchmode=source)

 



Recommend

lcy   |   We have carefully selected several similar problems for you:  [1035](http://acm.hdu.edu.cn/showproblem.php?pid=1035) [1071](http://acm.hdu.edu.cn/showproblem.php?pid=1071) [1032](http://acm.hdu.edu.cn/showproblem.php?pid=1032) [1548](http://acm.hdu.edu.cn/showproblem.php?pid=1548) [1031](http://acm.hdu.edu.cn/showproblem.php?pid=1031) 





Accepted Code

```java
package cn.edu.hdu.acm;

import java.util.Scanner;

public class Main1030 {

    public static void main(String[] args) {
        new Main1030().run();
    }

    private void run() {
        Scanner scanner = new Scanner(System.in);
        int m;
        int n;
        while (scanner.hasNextInt()) {
            m = scanner.nextInt();
            n = scanner.nextInt();
            if (m > n) {
                int temp = 0;
                temp = m;
                m = n;
                n = temp;
            }

            int rm = getRow(m);
            int lm = getColumn(m, rm);
            int rn = getRow(n);
            int ln = getColumn(n, rn);

            int out = 0;

            // 偶数时为倒三角形位置，将起点定位到上一个
            if (lm % 2 == 0) {
                rm -= 1;
                lm -= 1;
                out -= 1;
            }
            // st到en表示终点所在行，起点的控制范围
            int st = lm;
            int en = lm + (rn - rm) * 2;
            if (st <= ln && ln <= en) { // 终点在可控制范围内
                if (ln % 2 != 0)
                    out += 2 * (rn - rm);
                else {
                    out += 2 * (rn - rm) - 1;
                }
            } else { // 终点在可控制范围外
                if (ln < st) { // 可控范围的左边
                    if (st % 2 != 0)
                        out += 2 * (rn - rm);
                    else {
                        out += 2 * (rn - rm) - 1;
                    }
                    out += st - ln;
                }
                if (ln > en) { // 可控范围的右边
                    if (en % 2 != 0)
                        out += 2 * (rn - rm);
                    else {
                        out += 2 * (rn - rm) - 1;
                    }
                    out += ln - en;
                }
            }
            System.out.println(out);
        }
        scanner.close();
    }

    private int getRow(int v) {
        return (int) Math.ceil(Math.sqrt(v));
    }

    private int getColumn(int v, int r) {
        return v - (r - 1) * (r - 1);
    }

}
```

