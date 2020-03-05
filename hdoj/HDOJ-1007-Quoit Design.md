# Quoit Design

**Time Limit: 10000/5000 MS (Java/Others)    Memory Limit: 65536/32768 K (Java/Others)Total Submission(s): 72470    Accepted Submission(s): 19314**

Problem Description

Have you ever played quoit in a playground? Quoit is a game in which flat rings are pitched at some toys, with all the toys encircled awarded.
In the field of Cyberground, the position of each toy is fixed, and the ring is carefully designed so it can only encircle one toy at a time. On the other hand, to make the game look more attractive, the ring is designed to have the largest radius. Given a configuration of the field, you are supposed to find the radius of such a ring.

Assume that all the toys are points on a plane. A point is encircled by the ring if the distance between the point and the center of the ring is strictly less than the radius of the ring. If two toys are placed at the same point, the radius of the ring is considered to be 0.

 



Input

The input consists of several test cases. For each case, the first line contains an integer N (2 <= N <= 100,000), the total number of toys in the field. Then N lines follow, each contains a pair of (x, y) which are the coordinates of a toy. The input is terminated by N = 0.

 



Output

For each test case, print in one line the radius of the ring required by the Cyberground manager, accurate up to 2 decimal places. 

 



Sample Input

```
2
0 0
1 1
2
1 1
1 1
3
-1.5 0
0 0
0 1.5
0
```

 



Sample Output

```
0.71
0.00
0.75
```

 



Author

CHEN, Yue

 



Source

[ZJCPC2004](http://acm.hdu.edu.cn/search.php?field=problem&key=ZJCPC2004&source=1&searchmode=source)

 



Recommend

JGShining   |   We have carefully selected several similar problems for you:  [1006](http://acm.hdu.edu.cn/showproblem.php?pid=1006) [1009](http://acm.hdu.edu.cn/showproblem.php?pid=1009) [1008](http://acm.hdu.edu.cn/showproblem.php?pid=1008) [1010](http://acm.hdu.edu.cn/showproblem.php?pid=1010) [1011](http://acm.hdu.edu.cn/showproblem.php?pid=1011) 





Accepted Code

```java
//查找平面最近点对，经典分治法
package cn.edu.hdu.acm;

import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;
import java.io.OutputStreamWriter;
import java.io.PrintWriter;
import java.io.StreamTokenizer;
import java.util.Arrays;
import java.util.Comparator;

public class Main1007 {
    static int n;
	public static void main(String[] args) throws IOException {
		StreamTokenizer in=new StreamTokenizer(new BufferedReader(new InputStreamReader(System.in)));
		PrintWriter out = new PrintWriter(new OutputStreamWriter(System.out));
         while(in.nextToken()!=StreamTokenizer.TT_EOF)
         {
        	 n=(int)in.nval;if(n==0) {break;}
        	node no[]=new node[n];
        	
        	 for(int i=0;i<n;i++)
        	 {
        		 in.nextToken();double x=in.nval;
        		 in.nextToken();double y=in.nval;
        		 no[i]=new node(x,y);
        	 }
        	 Arrays.sort(no, com);
        	double min= search(no,0,n-1);
        	out.println(String.format("%.2f", Math.sqrt(min)/2));out.flush();
         }         
	}
	private static double search(node[] no, int left,int right) {
		int mid=(right+left)/2;//中间
        double minleng=0;
        if(left==right) {return Double.MAX_VALUE;}//一个点没有距离之说，返回最大不影响
        //相邻直接返回两点距离
        else if(left+1==right) {minleng= (no[left].x-no[right].x)*(no[left].x-no[right].x)+(no[left].y-no[right].y)*(no[left].y-no[right].y);}
        else minleng= min(search(no,left,mid),search(no,mid,right));//左右侧小的那个
        int ll=mid;int rr=mid+1;
        while(no[mid].y-no[ll].y<=Math.sqrt(minleng)/2&&ll-1>=left) {ll--;}//从中间向左找到不在距离内的那个点
        while(no[rr].y-no[mid].y<=Math.sqrt(minleng)/2&&rr+1<=right) {rr++;}//从中间向右找到不在距离内的那个带
        for(int i=ll;i<rr;i++)
        {
            for(int j=i+1;j<rr+1;j++)
            {
                double team=0;
                if(Math.abs((no[i].x-no[j].x)*(no[i].x-no[j].x))>minleng) {continue;}
                else
                { 
                    team=(no[i].x-no[j].x)*(no[i].x-no[j].x)+(no[i].y-no[j].y)*(no[i].y-no[j].y);
                    if(team<minleng)minleng=team;
                }
            }
        }
        return minleng;	
	}
	private static double min(double a, double b) {		
		return a<b?a:b;
	}
	static Comparator<node>com=new Comparator<node>() {	
		public int compare(node a1, node a2) {			
			return a1.y-a2.y>0?1:-1;
		}};
	static class node
	{
		double x;
		double y;
		public node(double x,double y)
		{
			this.x=x;
			this.y=y;
		}
	}
}
```

