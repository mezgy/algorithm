# Ignatius and the Princess I

**Time Limit: 2000/1000 MS (Java/Others)    Memory Limit: 65536/32768 K (Java/Others)Total Submission(s): 24169    Accepted Submission(s): 7791Special Judge**

Problem Description

The Princess has been abducted by the BEelzebub feng5166, our hero Ignatius has to rescue our pretty Princess. Now he gets into feng5166's castle. The castle is a large labyrinth. To make the problem simply, we assume the labyrinth is a N*M two-dimensional array which left-top corner is (0,0) and right-bottom corner is (N-1,M-1). Ignatius enters at (0,0), and the door to feng5166's room is at (N-1,M-1), that is our target. There are some monsters in the castle, if Ignatius meet them, he has to kill them. Here is some rules:

1.Ignatius can only move in four directions(up, down, left, right), one step per second. A step is defined as follow: if current position is (x,y), after a step, Ignatius can only stand on (x-1,y), (x+1,y), (x,y-1) or (x,y+1).
2.The array is marked with some characters and numbers. We define them like this:
. : The place where Ignatius can walk on.
X : The place is a trap, Ignatius should not walk on it.
n : Here is a monster with n HP(1<=n<=9), if Ignatius walk on it, it takes him n seconds to kill the monster.

Your task is to give out the path which costs minimum seconds for Ignatius to reach target position. You may assume that the start position and the target position will never be a trap, and there will never be a monster at the start position.

 



Input

The input contains several test cases. Each test case starts with a line contains two numbers N and M(2<=N<=100,2<=M<=100) which indicate the size of the labyrinth. Then a N*M two-dimensional array follows, which describe the whole labyrinth. The input is terminated by the end of file. More details in the Sample Input.

 



Output

For each test case, you should output "God please help our poor hero." if Ignatius can't reach the target position, or you should output "It takes n seconds to reach the target position, let me show you the way."(n is the minimum seconds), and tell our hero the whole path. Output a line contains "FINISH" after each test case. If there are more than one path, any one is OK in this problem. More details in the Sample Output.

 



Sample Input

```
5 6
.XX.1.
..X.2.
2...X.
...XX.
XXXXX.
5 6
.XX.1.
..X.2.
2...X.
...XX.
XXXXX1
5 6
.XX...
..XX1.
2...X.
...XX.
XXXXX.
```

 



Sample Output

```
It takes 13 seconds to reach the target position, let me show you the way.
1s:(0,0)->(1,0)
2s:(1,0)->(1,1)
3s:(1,1)->(2,1)
4s:(2,1)->(2,2)
5s:(2,2)->(2,3)
6s:(2,3)->(1,3)
7s:(1,3)->(1,4)
8s:FIGHT AT (1,4)
9s:FIGHT AT (1,4)
10s:(1,4)->(1,5)
11s:(1,5)->(2,5)
12s:(2,5)->(3,5)
13s:(3,5)->(4,5)
FINISH
It takes 14 seconds to reach the target position, let me show you the way.
1s:(0,0)->(1,0)
2s:(1,0)->(1,1)
3s:(1,1)->(2,1)
4s:(2,1)->(2,2)
5s:(2,2)->(2,3)
6s:(2,3)->(1,3)
7s:(1,3)->(1,4)
8s:FIGHT AT (1,4)
9s:FIGHT AT (1,4)
10s:(1,4)->(1,5)
11s:(1,5)->(2,5)
12s:(2,5)->(3,5)
13s:(3,5)->(4,5)
14s:FIGHT AT (4,5)
FINISH
God please help our poor hero.
FINISH
```

 



Author

Ignatius.L

 



Recommend

We have carefully selected several similar problems for you:  [1072](http://acm.hdu.edu.cn/showproblem.php?pid=1072) [1175](http://acm.hdu.edu.cn/showproblem.php?pid=1175) [1180](http://acm.hdu.edu.cn/showproblem.php?pid=1180) [1253](http://acm.hdu.edu.cn/showproblem.php?pid=1253) [1242](http://acm.hdu.edu.cn/showproblem.php?pid=1242) 





Accepted Code

```java
//BFS
package cn.edu.hdu.acm;

import java.util.*;
 
class Node {
	int x, y;
	int step;
	int id;
	int pre;
	boolean flag;
	Node(int x, int y, int id, int step, int pre, boolean flag){
		this.x = x;
		this.y = y;
		this.id = id;
		this.step = step;
		this.pre = pre;
		this.flag = flag;
	}
	public String toString() {
		return id + " " + x + " " + y + " " +step + " "  + pre + " " + flag;
	}
}
 
public class Main1026 {
 
	static int m, n;
	static final int maxn = 100 + 5;
	static char[][] maze = new char[maxn][maxn];
	static boolean[][] vis = new boolean[maxn][maxn];
	static int[][] dir = {{1, 0}, {-1, 0}, {0, 1}, {0, -1}};
	static Vector<Node>ans = new Vector<Node>();
	static Vector<Node>path = new Vector<Node>();
	
	static void getAns(int k) {
		if(path.elementAt(k).pre != -1)
			getAns(path.elementAt(k).pre);
		ans.add(path.elementAt(k));
	}
	
	static void print() {
		for(int i = 0; i < ans.size() - 1; ++i) {
			if(ans.elementAt(i).flag == true) {
				System.out.println(ans.elementAt(i).step+"s:FIGHT AT ("+ans.elementAt(i).x+","+ans.elementAt(i).y+")");
			}
		    if(ans.elementAt(i + 1).flag == false) {
				System.out.print((ans.elementAt(i).step + 1) + "s:");
				System.out.print("(" + ans.elementAt(i).x + "," + ans.elementAt(i).y + ")->");
				System.out.println("(" + ans.elementAt(i + 1).x + "," + ans.elementAt(i + 1).y + ")");
		    }
		}
		if(ans.lastElement().flag == true) {
			System.out.println(ans.lastElement().step+"s:FIGHT AT ("+ans.lastElement().x+","+ans.lastElement().y+")");
 
		}
	}
	
	static void bfs() {
		Queue<Node> q = new LinkedList<Node>();
		q.add(new Node(0, 0, 0, 0, -1, false));
		vis[0][0] = true;
		path.add(new Node(0, 0, 0, 0, -1, false));
		while(q.isEmpty() == false) {
			Node fr = q.remove();
			if((fr.x + 1) == n && (fr.y + 1) == m && (maze[fr.x][fr.y] == '.' || maze[fr.x][fr.y] == '0')) {
 
				System.out.println("It takes " + fr.step +" seconds to reach the target position, let me show you the way.");
				ans.clear();
				getAns(fr.id);
				print();
				System.out.println("FINISH");
				return;
			}
			if('1' <= maze[fr.x][fr.y] && maze[fr.x][fr.y] <= '9') {
				q.add(new Node(fr.x, fr.y, path.size(), fr.step + 1, fr.id, true));
				path.add(new Node(fr.x, fr.y, path.size(), fr.step + 1, fr.id, true));
				maze[fr.x][fr.y]--;
				vis[fr.x][fr.y] = true;
			} else {
				for(int i = 0; i < 4; i++) {
					int nx = fr.x + dir[i][0];
					int ny = fr.y + dir[i][1];
					if(0 <= nx && nx < n && 0 <= ny && ny < m && vis[nx][ny] == false && maze[nx][ny] != 'X') {
							q.add(new Node(nx, ny, path.size(), fr.step + 1, fr.id, false));
							path.add(new Node(nx, ny, path.size(), fr.step + 1, fr.id, false));
							vis[nx][ny] = true;
					}
				}
			}
		}
		System.out.println("God please help our poor hero.");
		System.out.println("FINISH");
	}
 
	public static void main(String[] args) {
		Scanner cin = new Scanner(System.in);
		while(cin.hasNextInt()) {
			n = cin.nextInt();
			m = cin.nextInt();
			
			String tmp;
			for(int i = 0; i < n; ++i) {
				tmp = cin.next();
				for(int j = 0; j < m; ++j)
					maze[i][j] = tmp.charAt(j);
			}
			for(int i = 0; i < maxn; ++i)
				Arrays.fill(vis[i], false);
			bfs();
		}
		cin.close();
	}
 
}
```

