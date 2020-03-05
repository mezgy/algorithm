# Collect More Jewels

**Time Limit: 2000/1000 MS (Java/Others)    Memory Limit: 65536/32768 K (Java/Others)Total Submission(s): 9293    Accepted Submission(s): 2197**

Problem Description

It is written in the Book of The Lady: After the Creation, the cruel god Moloch rebelled against the authority of Marduk the Creator.Moloch stole from Marduk the most powerful of all the artifacts of the gods, the Amulet of Yendor, and he hid it in the dark cavities of Gehennom, the Under World, where he now lurks, and bides his time.

Your goddess The Lady seeks to possess the Amulet, and with it to gain deserved ascendance over the other gods.

You, a newly trained Rambler, have been heralded from birth as the instrument of The Lady. You are destined to recover the Amulet for your deity, or die in the attempt. Your hour of destiny has come. For the sake of us all: Go bravely with The Lady!

If you have ever played the computer game NETHACK, you must be familiar with the quotes above. If you have never heard of it, do not worry. You will learn it (and love it) soon.

In this problem, you, the adventurer, are in a dangerous dungeon. You are informed that the dungeon is going to collapse. You must find the exit stairs within given time. However, you do not want to leave the dungeon empty handed. There are lots of rare jewels in the dungeon. Try collecting some of them before you leave. Some of the jewels are cheaper and some are more expensive. So you will try your best to maximize your collection, more importantly, leave the dungeon in time.

 



Input

Standard input will contain multiple test cases. The first line of the input is a single integer T (1 <= T <= 10) which is the number of test cases. T test cases follow, each preceded by a single blank line.

The first line of each test case contains four integers W (1 <= W <= 50), H (1 <= H <= 50), L (1 <= L <= 1,000,000) and M (1 <= M <= 10). The dungeon is a rectangle area W block wide and H block high. L is the time limit, by which you need to reach the exit. You can move to one of the adjacent blocks up, down, left and right in each time unit, as long as the target block is inside the dungeon and is not a wall. Time starts at 1 when the game begins. M is the number of jewels in the dungeon. Jewels will be collected once the adventurer is in that block. This does not cost extra time.

The next line contains M integers，which are the values of the jewels.

The next H lines will contain W characters each. They represent the dungeon map in the following notation:
\> [*] marks a wall, into which you can not move;
\> [.] marks an empty space, into which you can move;
\> [@] marks the initial position of the adventurer;
\> [<] marks the exit stairs;
\> [A] - [J] marks the jewels.

 



Output

Results should be directed to standard output. Start each case with "Case #:" on a single line, where # is the case number starting from 1. Two consecutive cases should be separated by a single blank line. No blank line should be produced after the last test case.

If the adventurer can make it to the exit stairs in the time limit, print the sentence "The best score is S.", where S is the maximum value of the jewels he can collect along the way; otherwise print the word "Impossible" on a single line.

 



Sample Input

```
3

4 4 2 2
100 200
****
*@A*
*B<*
****

4 4 1 2
100 200
****
*@A*
*B<*
****

12 5 13 2
100 200
************
*B.........*
*.********.*
*@...A....<*
************
```

 



Sample Output

```
Case 1:
The best score is 200.

Case 2:
Impossible

Case 3:
The best score is 300.
```

 



Source

[Asia 2005, Hangzhou (Mainland China), Preliminary](http://acm.hdu.edu.cn/search.php?field=problem&key=Asia+2005%2C+Hangzhou+(Mainland+China)%2C+Preliminary&source=1&searchmode=source)

 



Recommend

JGShining   |   We have carefully selected several similar problems for you:  [1072](http://acm.hdu.edu.cn/showproblem.php?pid=1072) [1180](http://acm.hdu.edu.cn/showproblem.php?pid=1180) [1195](http://acm.hdu.edu.cn/showproblem.php?pid=1195) [1175](http://acm.hdu.edu.cn/showproblem.php?pid=1175) [1401](http://acm.hdu.edu.cn/showproblem.php?pid=1401) 

 



Accepted Code

```java
package cn.edu.hdu.acm;

import java.util.*;

public class Main1044 {

    static int n, m;
    static int max = 0, sum = 0;
    static int totalTime, ex, ey;
    static int dirArr[][] = new int[][] { { 1, 0 }, { 0, 1 }, { -1, 0 }, { 0, -1 } };
    static char[][] map;
    static int[] value;
    static int[][] adj = new int[14][14];
    static boolean visit[];
    static boolean visadj[][];
    static Node[] nodes;
    static int num;

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int T = sc.nextInt();
        for (int i = 1; i <= T; i++) {
            max = 0;
            sum = 0;
            nodes = new Node[13];
            visit = new boolean[15];
            m = sc.nextInt();
            n = sc.nextInt();
            totalTime = sc.nextInt();
            num = sc.nextInt();
            value = new int[num];
            map = new char[n][m];
            int sx = 0, sy = 0;
            for (int k = 0; k < num; k++) {
                value[k] = sc.nextInt();
            }
            for (int k = 0; k < n; k++) {
                char[] arr = sc.next().toCharArray();
                for (int j = 0; j < m; j++) {
                    char temp = arr[j];
                    map[k][j] = temp;
                    if (temp == '@') {
                        sx = k;
                        sy = j;
                    } else if (temp == '<') {
                        ex = k;
                        ey = j;
                    } else if (temp >= 'A' && temp <= 'J') {
                        nodes[temp - 'A'] = new Node(k, j, 0);
                    }
                }
            }
            InitArray();
            BFS(sx, sy, num);
            if (i > 1) {
                System.out.println();
            }
            System.out.println("Case " + i + ":");
            if (adj[num][num + 1] == -1 || adj[num][num + 1] > totalTime) {
                System.out.println("Impossible");
                continue;
            }

            for (int kk = 0; kk < num; kk++) {
                if (adj[kk][num] != -1) {
                    sum += value[kk];
                }
            }
            BFS(ex, ey, num + 1);
            for (int k = 0; k < num; k++) {
                BFS(nodes[k].x, nodes[k].y, k);
            }
            visit[num] = true;
            DFS(num, 0, 0);
            System.out.println("The best score is " + max + ".");
        }

    }

    static void InitArray() {
        for (int i = 0; i < 14; i++) {
            for (int j = 0; j < 14; j++) {
                adj[i][j] = -1;
            }
        }
    }

    static void DFS(int i, int step, int val) {
        if (step > totalTime || max == sum) {
            return;
        }
        if (i == num + 1) {
            if (val > max) {
                max = val;
            }
        }
        if (i != num + 1 && step + adj[i][num + 1] > totalTime) {
            return;
        }
        for (int j = 0; j <= num + 1; j++) {
            if (adj[i][j] != -1) {
                if (visit[j]) {
                    continue;
                }
                visit[j] = true;
                if (j < num) {
                    DFS(j, step + adj[i][j], val + value[j]);
                } else {
                    DFS(j, step + adj[i][j], val);
                }
                visit[j] = false;
            }
        }
    }

    static void BFS(int x0, int y0, int k) {
        Queue<Node> queue = new ArrayDeque<Node>();
        queue.add(new Node(x0, y0, 0));
        visadj = new boolean[55][55];
        visadj[x0][y0] = true;
        while (!queue.isEmpty()) {
            Node pre = queue.poll();
            for (int i = 0; i < 4; i++) {
                Node curr = new Node(pre.x, pre.y, pre.step);
                curr.x += dirArr[i][0];
                curr.y += dirArr[i][1];
                int x = curr.x;
                int y = curr.y;
                curr.step++;
                if (x < 0 || x >= n || y < 0 || y >= m || map[x][y] == '*'
                        || visadj[x][y]) {
                    continue;
                }
                visadj[x][y] = true;
                queue.add(curr);
                if (map[x][y] >= 'A' && map[x][y] <= 'J') {
                    int index = map[x][y] - 'A';
                    adj[index][k] = adj[k][index] = curr.step;
                } else if (map[x][y] == '@') {
                    adj[k][num] = adj[num][k] = curr.step;
                } else if (map[x][y] == '<') {
                    adj[k][num + 1] = adj[num + 1][k] = curr.step;
                }
            }
        }
    }

    static class Node {
        protected int x, y;
        protected int step;
        protected boolean isVisit;

        public Node(int x, int y, int step) {
            this.x = x;
            this.y = y;
            this.step = step;
        }
    }
}


```

