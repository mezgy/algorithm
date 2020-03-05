# Edge

**Time Limit: 2000/1000 MS (Java/Others)    Memory Limit: 65536/32768 K (Java/Others)Total Submission(s): 5378    Accepted Submission(s): 3215**

Problem Description

For products that are wrapped in small packings it is necessary that the sheet of paper containing the directions for use is folded until its size becomes small enough. We assume that a sheet of paper is rectangular and only folded along lines parallel to its initially shorter edge. The act of folding along such a line, however, can be performed in two directions: either the surface on the top of the sheet is brought together, or the surface on its bottom. In both cases the two parts of the rectangle that are separated by the folding line are laid together neatly and we ignore any differences in thickness of the resulting folded sheet. 
After several such folding steps have been performed we may unfold the sheet again and take a look at its longer edge holding the sheet so that it appears as a one-dimensional curve, actually a concatenation of line segments. If we move along this curve in a fixed direction we can classify every place where the sheet was folded as either type A meaning a clockwise turn or type V meaning a counter-clockwise turn. Given such a sequence of classifications, produce a drawing of the longer edge of the sheet assuming 90 degree turns at equidistant places.

 



Input

The input contains several test cases, each on a separate line. Each line contains a nonempty string of characters A and V describing the longer edge of the sheet. You may assume that the length of the string is less than 200. The input file terminates immediately after the last test case.

 



Output

For each test case generate a PostScript drawing of the edge with commands placed on separate lines. Start every drawing at the coordinates (300, 420) with the command "300 420 moveto". The first turn occurs at (310, 420) using the command "310 420 lineto". Continue with clockwise or counter-clockwise turns according to the input string, using a sequence of "x y lineto" commands with the appropriate coordinates. The turning points are separated at a distance of 10 units. Do not forget the end point of the edge and finish each test case by the commands stroke and showpage. 

You may display such drawings with the gv PostScript interpreter, optionally after a conversion using the ps2ps utility.

![img](http://acm.hdu.edu.cn/data/images/1033-1.gif)

 



Sample Input

```
V
AVV
```

 



Sample Output

```
300 420 moveto
310 420 lineto
310 430 lineto
stroke
showpage
300 420 moveto
310 420 lineto
310 410 lineto
320 410 lineto
320 420 lineto
stroke
showpage
```

 



Source

[University of Ulm Local Contest 2003](http://acm.hdu.edu.cn/search.php?field=problem&key=University+of+Ulm+Local+Contest+2003&source=1&searchmode=source)

 



Recommend

We have carefully selected several similar problems for you:  [1035](http://acm.hdu.edu.cn/showproblem.php?pid=1035) [1036](http://acm.hdu.edu.cn/showproblem.php?pid=1036) [1039](http://acm.hdu.edu.cn/showproblem.php?pid=1039) [1062](http://acm.hdu.edu.cn/showproblem.php?pid=1062) [1073](http://acm.hdu.edu.cn/showproblem.php?pid=1073) 

 



Accepted Code

```java
package cn.edu.hdu.acm;

import java.util.Scanner;

public class Main1033 {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        while (sc.hasNext()) {
            String str = sc.next();
            System.out.println("300 420 moveto");
            System.out.println("310 420 lineto");
            int x = 310;
            int y = 420;
            int dirct = 1;
            // 1左，3右，0上，2下
            int i = 0;
            while (i < str.length()) {
                if (str.charAt(i) == 'A') {
                    dirct = (dirct + 1) % 4;
                } else {
                    dirct = (dirct - 1 + 4) % 4;
                }
                switch (dirct) {
                    case 0:
                        y += 10;
                        break;
                    case 1:
                        x += 10;
                        break;
                    case 2:
                        y -= 10;
                        break;
                    case 3:
                        x -= 10;
                        break;
                }
                System.out.println(x+" "+y+" lineto");
                i++;
            }
            System.out.println("stroke");
            System.out.println("showpage");
        }
        sc.close();
    }

}

```

