# Design T-Shirt

**Time Limit: 2000/1000 MS (Java/Others)    Memory Limit: 65536/32768 K (Java/Others)Total Submission(s): 14382    Accepted Submission(s): 6920**

Problem Description

Soon after he decided to design a T-shirt for our Algorithm Board on Free-City BBS, XKA found that he was trapped by all kinds of suggestions from everyone on the board. It is indeed a mission-impossible to have everybody perfectly satisfied. So he took a poll to collect people's opinions. Here are what he obtained: N people voted for M design elements (such as the ACM-ICPC logo, big names in computer science, well-known graphs, etc.). Everyone assigned each element a number of satisfaction. However, XKA can only put K (<=M) elements into his design. He needs you to pick for him the K elements such that the total number of satisfaction is maximized.

 



Input

The input consists of multiple test cases. For each case, the first line contains three positive integers N, M and K where N is the number of people, M is the number of design elements, and K is the number of elements XKA will put into his design. Then N lines follow, each contains M numbers. The j-th number in the i-th line represents the i-th person's satisfaction on the j-th element.

 



Output

For each test case, print in one line the indices of the K elements you would suggest XKA to take into consideration so that the total number of satisfaction is maximized. If there are more than one solutions, you must output the one with minimal indices. The indices start from 1 and must be printed in non-increasing order. There must be exactly one space between two adjacent indices, and no extra space at the end of the line.

 



Sample Input

```
3 6 4
2 2.5 5 1 3 4
5 1 3.5 2 2 2
1 1 1 1 1 10
3 3 2
1 2 3
2 3 1
3 1 2
```

 



Sample Output

```
6 5 3 1
2 1
```

 



Author

CHEN, Yue

 



Source

[CYJJ's Funny Contest #1, Killing in Seconds](http://acm.hdu.edu.cn/search.php?field=problem&key=CYJJ's+Funny+Contest+%231%2C+Killing+in+Seconds&source=1&searchmode=source)

 



Recommend

Ignatius.L   |   We have carefully selected several similar problems for you:  [1036](http://acm.hdu.edu.cn/showproblem.php?pid=1036) [1032](http://acm.hdu.edu.cn/showproblem.php?pid=1032) [1033](http://acm.hdu.edu.cn/showproblem.php?pid=1033) [1037](http://acm.hdu.edu.cn/showproblem.php?pid=1037) [1039](http://acm.hdu.edu.cn/showproblem.php?pid=1039) 





Accepted Code

```java
package cn.edu.hdu.acm;

import java.util.Arrays;
import java.util.Comparator;
import java.util.Scanner;

public class Main1031 {

    public static void main(String[] args) {
        new Main1031().run();
    }

    public void run(){
        Scanner scanner = new Scanner(System.in);
        int N, M, K;
        node[] nodes;
        while (scanner.hasNextInt()) {
            N = scanner.nextInt();
            M = scanner.nextInt();
            K = scanner.nextInt();
            nodes = new node[M];
            for (int i = 0; i < M; i++) {
                nodes[i] = new node();
                nodes[i].id = i + 1;
                nodes[i].score = 0;
            }
            for (int i = 0; i < N; i++) {
                for (int j = 0; j < M; j++) {
                    nodes[j].score += scanner.nextDouble();
                }
            }
            Arrays.sort(nodes, new Comparator<node>() {

                @Override
                public int compare(node o1, node o2) {
                    return o1.score > o2.score ? -1 : 1;
                }
            });
            Arrays.sort(nodes, 0, K ,new Comparator<node>() {
                @Override
                public int compare(node o1, node o2) {
                    return o1.id > o2.id ? -1 : 1;
                }
            });
            int i;
            for (i = 0; i < K - 1; i++) {
                System.out.print(nodes[i].id + " ");
            }
            System.out.println(nodes[i].id);
        }
        scanner.close();
    }

    class node{
        int id;
        double score;
    }

}
```

