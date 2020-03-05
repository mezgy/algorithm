# Constructing Roads In JGShining's Kingdom

**Time Limit: 2000/1000 MS (Java/Others)    Memory Limit: 65536/32768 K (Java/Others)Total Submission(s): 32782    Accepted Submission(s): 9235**

Problem Description

JGShining's kingdom consists of 2n(n is no more than 500,000) small cities which are located in two parallel lines.

Half of these cities are rich in resource (we call them rich cities) while the others are short of resource (we call them poor cities). Each poor city is short of exactly one kind of resource and also each rich city is rich in exactly one kind of resource. You may assume no two poor cities are short of one same kind of resource and no two rich cities are rich in one same kind of resource.

With the development of industry, poor cities wanna import resource from rich ones. The roads existed are so small that they're unable to ensure the heavy trucks, so new roads should be built. The poor cities strongly BS each other, so are the rich ones. Poor cities don't wanna build a road with other poor ones, and rich ones also can't abide sharing an end of road with other rich ones. Because of economic benefit, any rich city will be willing to export resource to any poor one.

Rich citis marked from 1 to n are located in Line I and poor ones marked from 1 to n are located in Line II.

The location of Rich City 1 is on the left of all other cities, Rich City 2 is on the left of all other cities excluding Rich City 1, Rich City 3 is on the right of Rich City 1 and Rich City 2 but on the left of all other cities ... And so as the poor ones.

But as you know, two crossed roads may cause a lot of traffic accident so JGShining has established a law to forbid constructing crossed roads.

For example, the roads in Figure I are forbidden.

![img](http://acm.hdu.edu.cn/data/images/1025-1.png)

In order to build as many roads as possible, the young and handsome king of the kingdom - JGShining needs your help, please help him. ^_^

 



Input

Each test case will begin with a line containing an integer n(1 ≤ n ≤ 500,000). Then n lines follow. Each line contains two integers p and r which represents that Poor City p needs to import resources from Rich City r. Process to the end of file.

 



Output

For each test case, output the result in the form of sample.
You should tell JGShining what's the maximal number of road(s) can be built.

 



Sample Input

```
2
1 2
2 1
3
1 2
2 3
3 1
```

 



Sample Output

```
Case 1:
My king, at most 1 road can be built.

Case 2:
My king, at most 2 roads can be built.

Hint
Huge input, scanf is recommended.
 
```

 



Author

JGShining（极光炫影）

 



Recommend

We have carefully selected several similar problems for you:  [1081](http://acm.hdu.edu.cn/showproblem.php?pid=1081) [1074](http://acm.hdu.edu.cn/showproblem.php?pid=1074) [1078](http://acm.hdu.edu.cn/showproblem.php?pid=1078) [1080](http://acm.hdu.edu.cn/showproblem.php?pid=1080) [1114](http://acm.hdu.edu.cn/showproblem.php?pid=1114) 

 



Accepted Code

```java
//此题应该AC了，但是oj提交这道题总是提交不了，无法验证
package cn.edu.hdu.acm;

import java.io.BufferedReader;
import java.io.InputStreamReader;

public class Main1025 {

	public static void main(String[] args)  {
        try{
            BufferedReader br = new BufferedReader(new InputStreamReader(System.in ));
            int count = 1;	
            String s;
            while (true) {
                s = br.readLine();
                if(s.equals(""))
                    continue;
                int n = Integer.parseInt(s.trim());

                int[] data = new int[n];
                for(int i = 0;i < n;i++){
                    String str = br.readLine().trim();
                    String[] strings = str.split(" ");
                    int f = 0;
                    int s1 = 0,s2 = 0;
                    for(int j = 0;j < strings.length;j++){
                        if(!strings[j].equals("")&&f ==0){
                            s1 = Integer.parseInt(strings[j]);
                            f = 1;
                        }
                        else if(!strings[j].equals("")&&f==1){
                            s2 = Integer.parseInt(strings[j]);
                        }

                    }
                    data[s1-1] = s2;
                }

                int[] B = new int[n];
                int len = 1;
                B[0] = data[0];
                for (int i = 1;i < n;i++){
                    int result = search(B,0,len-1,data[i]);
                    if(result == 1){
                        len++;
                    }
                }
                if(len>1){
                    System.out.println("Case "+count+":");
                    System.out.println("My king, at most "+len+" roads can be built.");
                    System.out.println();
                }
                else{
                    System.out.println("Case "+count+":");
                    System.out.println("My king, at most "+len+" road can be built.");
                    System.out.println();
                }
                count++;
            }
        }catch (Exception e){
        	
        }
    }

    public static int search(int[] a, int h, int e, int number) {
        if (e == h) {
            if (a[e] > number) {
                a[e] = number;
                return 0;
            } else if (a[e] < number) {
                a[e + 1] = number;
                return 1;
            } else
                return -1;
        } else {
            int mid = 0;
            int result = 0;
            while (e != h) {
                mid = (e + h) / 2;
                if (a[mid] == number) {
                    result = mid;
                    break;
                } else if (a[mid] > number) {
                    e = mid;
                    result = e;
                } else {
                    h = mid + 1;
                    result = h;
                }
            }
            if (a[result] > number) {
                a[result] = number;
                return 0;
            } else if (a[result] < number) {
                a[result + 1] = number;
                return 1;
            } else {
                return -1;
            }
        }
    }
}
```

