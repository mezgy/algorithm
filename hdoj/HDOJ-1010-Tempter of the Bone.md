# Tempter of the Bone

**Time Limit: 2000/1000 MS (Java/Others)    Memory Limit: 65536/32768 K (Java/Others)Total Submission(s): 166920    Accepted Submission(s): 44306**

Problem Description

The doggie found a bone in an ancient maze, which fascinated him a lot. However, when he picked it up, the maze began to shake, and the doggie could feel the ground sinking. He realized that the bone was a trap, and he tried desperately to get out of this maze.

The maze was a rectangle with sizes N by M. There was a door in the maze. At the beginning, the door was closed and it would open at the T-th second for a short period of time (less than 1 second). Therefore the doggie had to arrive at the door on exactly the T-th second. In every second, he could move one block to one of the upper, lower, left and right neighboring blocks. Once he entered a block, the ground of this block would start to sink and disappear in the next second. He could not stay at one block for more than one second, nor could he move into a visited block. Can the poor doggie survive? Please help him.

 



Input

The input consists of multiple test cases. The first line of each test case contains three integers N, M, and T (1 < N, M < 7; 0 < T < 50), which denote the sizes of the maze and the time at which the door will open, respectively. The next N lines give the maze layout, with each line containing M characters. A character is one of the following:

'X': a block of wall, which the doggie cannot enter;
'S': the start point of the doggie;
'D': the Door; or
'.': an empty block.

The input is terminated with three 0's. This test case is not to be processed.

 



Output

For each test case, print in one line "YES" if the doggie can survive, or "NO" otherwise.

 



Sample Input

```
4 4 5
S.X.
..X.
..XD
....
3 4 5
S.X.
..X.
...D
0 0 0
```

 



Sample Output

```
NO
YES
```

 



Author

ZHANG, Zheng

 



Source

[ZJCPC2004](http://acm.hdu.edu.cn/search.php?field=problem&key=ZJCPC2004&source=1&searchmode=source)

 



Recommend

JGShining   |   We have carefully selected several similar problems for you:  [1016](http://acm.hdu.edu.cn/showproblem.php?pid=1016) [1241](http://acm.hdu.edu.cn/showproblem.php?pid=1241) [1242](http://acm.hdu.edu.cn/showproblem.php?pid=1242) [1072](http://acm.hdu.edu.cn/showproblem.php?pid=1072) [1312](http://acm.hdu.edu.cn/showproblem.php?pid=1312) 





Accepted Code

```java
package cn.edu.hdu.acm;

import java.util.Scanner;

public class Main1010 {


    static int N, M, T, endI, endJ;
    static boolean[][] visited;
    static boolean ans;

    static void memset(boolean[][] arr, boolean bo) {
        int height = arr.length;
        int width = arr[0].length;
        for (int i = 0; i < height; i++) {
            for (int j = 0; j < width; j++) {
                arr[i][j] = bo;
            }
        }
    }

    static void DFS(int i, int j, int count) {
        if (ans)
            return;
        if (count > T)
            return;
        if (i < 0 || j < 0 || i >= N || j >= M)
            return;
        if (i == endI && j == endJ && count == T) {
            ans = true;
            return;
        }

        // 奇偶剪枝
        int temp = Math.abs(endI - i) + Math.abs(endJ - j);
        temp = T - count - temp;
        if ((temp & 1) == 1)
            return;

        if ((i - 1 >= 0) && !visited[i - 1][j]) {
            visited[i - 1][j] = true;
            DFS(i - 1, j, count + 1);
            visited[i - 1][j] = false;
        }
        if ((i + 1 < N) && !visited[i + 1][j]) {
            visited[i + 1][j] = true;
            DFS(i + 1, j, count + 1);
            visited[i + 1][j] = false;
        }
        if ((j - 1 >= 0) && !visited[i][j - 1]) {
            visited[i][j - 1] = true;
            DFS(i, j - 1, count + 1);
            visited[i][j - 1] = false;
        }
        if ((j + 1 < M) && !visited[i][j + 1]) {
            visited[i][j + 1] = true;
            DFS(i, j + 1, count + 1);
            visited[i][j + 1] = false;
        }
    }

    public static void main(String[] args) {
        Scanner cin = new Scanner(System.in);
        int startX = 0, startY = 0;
        while (cin.hasNext()) {
            N = cin.nextInt();
            M = cin.nextInt();
            T = cin.nextInt();
            if (N == 0 || M == 0 || T == 0)
                return;
            ans = false;
            visited = new boolean[N][M];
            memset(visited, false);

            int k = 0;

            for (int i = 0; i < N; i++) {
                String str;
                str = cin.next();
                for (int j = 0; j < M; j++) {
                    char ch = str.charAt(j);
                    if (ch == 'X') {
                        visited[i][j] = true;
                        k++;
                    } else if (ch == 'D') {
                        endI = i;
                        endJ = j;
                    } else if (ch == 'S') {
                        startX = i;
                        startY = j;
                        visited[i][j] = true;
                    }
                }
            }

            visited[startX][startY] = true;

            if (N * M - k - 1 >= T)
                DFS(startX, startY, 0);
            if (ans) {
                System.out.println("YES");
            } else {
                System.out.println("NO");
            }

        }
    }
}
```

