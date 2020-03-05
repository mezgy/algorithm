# Let the Balloon Rise

**Time Limit: 2000/1000 MS (Java/Others)    Memory Limit: 65536/32768 K (Java/Others)Total Submission(s): 166580    Accepted Submission(s): 66385**

Problem Description

Contest time again! How excited it is to see balloons floating around. But to tell you a secret, the judges' favorite time is guessing the most popular problem. When the contest is over, they will count the balloons of each color and find the result.

This year, they decide to leave this lovely job to you. 

 



Input

Input contains multiple test cases. Each test case starts with a number N (0 < N <= 1000) -- the total number of balloons distributed. The next N lines contain one color each. The color of a balloon is a string of up to 15 lower-case letters.

A test case with N = 0 terminates the input and this test case is not to be processed.

 



Output

For each case, print the color of balloon for the most popular problem on a single line. It is guaranteed that there is a unique solution for each test case.

 



Sample Input

```
5
green
red
blue
red
red
3
pink
orange
pink
0
```

 



Sample Output

```
red
pink
```

 



Author

WU, Jiazhi

 



Source

[ZJCPC2004](http://acm.hdu.edu.cn/search.php?field=problem&key=ZJCPC2004&source=1&searchmode=source)

 



Recommend

JGShining   |   We have carefully selected several similar problems for you:  [1008](http://acm.hdu.edu.cn/showproblem.php?pid=1008) [1005](http://acm.hdu.edu.cn/showproblem.php?pid=1005) [1009](http://acm.hdu.edu.cn/showproblem.php?pid=1009) [1019](http://acm.hdu.edu.cn/showproblem.php?pid=1019) [1021](http://acm.hdu.edu.cn/showproblem.php?pid=1021) 





Accepted Code

```java
package cn.edu.hdu.acm;

import java.util.*;

public class Main1004{
    public static void main(String[] args) throws Exception{
        Scanner cin = new Scanner(System.in);
        //控制测试用例
        while(cin.hasNextInt())
        {   
            int num  = cin.nextInt();
            //输入0结束测试
            if(num<=0)
                break;
            //输入测试数据
            List<Item> items = new ArrayList<Item>();
            for(int i = 0;i<num;i++){
                String item = cin.next();
                boolean flag = false;

                for(int j = 0;j<items.size();j++){
                    //当前集合中包含输入的气球
                    if(items.get(j).str.equals(item)){
                        items.get(j).count+=1;
                        flag = true;
                        break;
                    }
                }
                //当前集合中不包含输入的气球
                if(!flag){
                    items.add(new Item(item,1));
                }
            }
            //找出最多气球的气球个数
            int max = items.get(0).count;
            for(int i = 1;i<items.size();i++){
                if(items.get(i).count>max){
                    max = items.get(i).count;
                }
            }
            //输出所有的最多的气球
            for(int i = 0;i<items.size();i++){
                if(items.get(i).count == max){
                    System.out.println(items.get(i).str);
                }

            }
        }

    }
}
class Item{
    public String str;
    public int count;
    public Item(String s,int c){
        str = s;
        count= c;
    }
}
```

