# Candy Sharing Game

**Time Limit: 2000/1000 MS (Java/Others)    Memory Limit: 65536/32768 K (Java/Others)Total Submission(s): 10841    Accepted Submission(s): 6226**

Problem Description

A number of students sit in a circle facing their teacher in the center. Each student initially has an even number of pieces of candy. When the teacher blows a whistle, each student simultaneously gives half of his or her candy to the neighbor on the right. Any student, who ends up with an odd number of pieces of candy, is given another piece by the teacher. The game ends when all students have the same number of pieces of candy.
Write a program which determines the number of times the teacher blows the whistle and the final number of pieces of candy for each student from the amount of candy each child starts with.

 



Input

The input may describe more than one game. For each game, the input begins with the number N of students, followed by N (even) candy counts for the children counter-clockwise around the circle. The input ends with a student count of 0. Each input number is on a line by itself.

 



Output

For each game, output the number of rounds of the game followed by the amount of candy each child ends up with, both on one line.

 



Sample Input

```
6
36
2
2
2
2
2
11
22
20
18
16
14
12
10
8
6
4
2
4
2
4
6
8
0
```

 



Sample Output

```
15 14
17 22
4 8

Hint
The game ends in a finite number of steps because:
1. The maximum candy count can never increase.
2. The minimum candy count can never decrease.
3. No one with more than the minimum amount will ever decrease to the minimum.
4. If the maximum and minimum candy count are not the same, at least one student with the minimum amount must have their count increase.
 
```

 



Source

[Greater New York 2003](http://acm.hdu.edu.cn/search.php?field=problem&key=Greater+New+York+2003&source=1&searchmode=source)

 



Recommend

We have carefully selected several similar problems for you:  [1037](http://acm.hdu.edu.cn/showproblem.php?pid=1037) [1038](http://acm.hdu.edu.cn/showproblem.php?pid=1038) [1036](http://acm.hdu.edu.cn/showproblem.php?pid=1036) [1073](http://acm.hdu.edu.cn/showproblem.php?pid=1073) [1062](http://acm.hdu.edu.cn/showproblem.php?pid=1062) 

 



Accepted Code

```java
package cn.edu.hdu.acm;

import java.util.Scanner;

public class Main1034 {

    public static void main(String[] args) {
        Scanner scanner =  new Scanner(System.in);

        while (scanner.hasNextInt()) {
            int n = scanner.nextInt();
            if (n==0) {
                break;
            }

            int arr[] = new int[n];
            for (int i=0;i<n;i++) {
                arr[i] = scanner.nextInt();
            }
            f(arr);
        }
    }

    //分糖果
    private static void f(int[] arr) {
        int temp = 0;
        while (!same(arr)) {
            int n = arr[arr.length-1];
            for (int i=arr.length-1;i>0;i--) {
                arr[i] = arr[i]/2+arr[i-1]/2;

            }
            arr[0] = arr[0]/2+n/2;
            g(arr);
            temp++;
        }
        System.out.println((temp)+" "+(arr[0]));
    }

    //奇数加一
    private static void g(int[] arr) {
        for(int i=0;i<arr.length;i++) {
            if (arr[i]%2!=0) {
                arr[i]++;
            }
        }
    }

    //是否糖果数相同
    private static boolean same(int[] arr) {
        int temp = 1;
        for (int i=1;i<arr.length;i++) {
            if (arr[0]!=arr[i]) {
                temp = 0;
                break;
            }
        }
        if (temp==1) {
            return true;
        }
        return false;
    }
}

```

