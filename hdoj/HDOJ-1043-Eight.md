# Eight

**Time Limit: 10000/5000 MS (Java/Others)    Memory Limit: 65536/32768 K (Java/Others)Total Submission(s): 36787    Accepted Submission(s): 9429Special Judge**

Problem Description

The 15-puzzle has been around for over 100 years; even if you don't know it by that name, you've seen it. It is constructed with 15 sliding tiles, each with a number from 1 to 15 on it, and all packed into a 4 by 4 frame with one tile missing. Let's call the missing tile 'x'; the object of the puzzle is to arrange the tiles so that they are ordered as:




Not all puzzles can be solved; in 1870, a man named Sam Loyd was famous for distributing an unsolvable version of the puzzle, andfrustrating many people. In fact, all you have to do to make a regular puzzle into an unsolvable one is to swap two tiles (not counting the missing 'x' tile, of course).



 



Input

You will receive, several descriptions of configuration of the 8 puzzle. One description is just a list of the tiles in their initial positions, with the rows listed from top to bottom, and the tiles listed from left to right within a row, where the tiles are represented by numbers 1 to 8, plus 'x'. For example, this puzzle

1 2 3
x 4 6
7 5 8

is described by this list:

1 2 3 x 4 6 7 5 8

 



Output

You will print to standard output either the word ``unsolvable'', if the puzzle has no solution, or a string consisting entirely of the letters 'r', 'l', 'u' and 'd' that describes a series of moves that produce a solution. The string should include no spaces and start at the beginning of the line. Do not print a blank line between cases.

 



Sample Input

```
2  3  4  1  5  x  7  6  8
```

 



Sample Output

```
ullddrurdllurdruldr
```

 



Source

[South Central USA 1998 (Sepcial Judge Module By JGShining)](http://acm.hdu.edu.cn/search.php?field=problem&key=South+Central+USA+1998+(Sepcial+Judge+Module+By+JGShining)&source=1&searchmode=source)

 



Recommend

JGShining   |   We have carefully selected several similar problems for you:  [1044](http://acm.hdu.edu.cn/showproblem.php?pid=1044) [1072](http://acm.hdu.edu.cn/showproblem.php?pid=1072) [1180](http://acm.hdu.edu.cn/showproblem.php?pid=1180) [1067](http://acm.hdu.edu.cn/showproblem.php?pid=1067) [1401](http://acm.hdu.edu.cn/showproblem.php?pid=1401) 





Accepted Code

```java
package cn.edu.hdu.acm;

import java.util.Scanner;
import java.util.LinkedList;

public class Main1043 {
    static int[] fac={1,1,2,6,24,120,720,5040,40320,362880};
    static NodeWay[] nn=new NodeWay[363000];
    static int[][] dir={{0,1},{1,0},{-1,0},{0,-1}};

    public static void main(String[] args) {
        Scanner cin=new Scanner(System.in);
        for(int i=0;i<nn.length;i++) {
            nn[i]=new NodeWay();
            nn[i].Father=-1;
        }
        bfs();
        while(cin.hasNext()) {
            int[] cc=new int[9];
            int count=0;
            String str=cin.nextLine();
            for(int i=0;i<str.length();i++) {
                if(str.charAt(i)==' '){
                    continue;
                }
                if(str.charAt(i)=='x'){
                    cc[count++]=0;
                }else{
                    cc[count++]=Integer.valueOf(str.charAt(i)+"");
                }
            }
            int cantorr=cantor(cc,9);
            if(nn[cantorr].Father==-1) {
                System.out.println("unsolvable");
            }
            else{
                while(nn[cantorr].Father!=0) {
                    System.out.print(nn[cantorr].Way);
                    cantorr=nn[cantorr].Father;
                }
                System.out.println();
            }
        }
    }

    static int cantor(int[] number,int n)
    {
        int result=0;
        for(int i=0;i<n;i++) {
            int count=0;
            for(int j=i+1;j<n;j++) {
                if(number[i]>number[j]){
                    count++;
                }
            }
            result+=count*fac[n-i-1];
        }
        return result+1;
    }

    static void bfs()    //从123456780的末状态开始往之前的状态搜，搜出一种不同的就给他存起来
    {
        Node start=new Node();
        start.CantorValue=46234;
        for(int i=0;i<9;i++) {
            start.map[i]=(i+1)%9;
        }
        start.loc=8;
        nn[46234].Father=0;
        int row;
        int col;
        LinkedList<Node> queue=new LinkedList<Node>();
        queue.add(start);
        while(!queue.isEmpty()) {
            Node node=queue.poll();
            for(int i=0;i<4;i++) {
                row=node.loc/3+dir[i][0];
                col=node.loc%3+dir[i][1];
                if(row<0||col<0||row>=3||col>=3){
                    continue;
                }
                Node work=new Node();
                work.CantorValue=node.CantorValue;
                work.loc=node.loc;
                for(int k=0;k<9;k++){
                    work.map[k]=node.map[k];
                }
                work.loc=row*3+col;
                int temp=0;
                temp=work.map[node.loc];
                work.map[node.loc]=work.map[work.loc];
                work.map[work.loc]=temp;
                work.CantorValue=cantor(work.map,9);
                if(nn[work.CantorValue].Father==-1) {
                    nn[work.CantorValue].Father=node.CantorValue;
                    if(i==0) {
                        nn[work.CantorValue].Way='l';
                    }
                    if(i==1) {
                        nn[work.CantorValue].Way='u';
                    }
                    if (i != 2) {
                    } else {
                        nn[work.CantorValue].Way='d';
                    }
                    if(i==3) {
                        nn[work.CantorValue].Way='r';
                    }
                    queue.offer(work);
                }
            }
        }
    }
}

class NodeWay
{
    char Way;
    int Father;
    NodeWay(){}
}

class Node
{
    int CantorValue;           //康托值
    int[] map=new int[9];      //当前状态。用一维数组表示。
    int loc;     //标记出x的位置，方便操作
    Node(){}
}

```

