# Train Problem I

**Time Limit: 2000/1000 MS (Java/Others)    Memory Limit: 65536/32768 K (Java/Others)Total Submission(s): 54901    Accepted Submission(s): 20624**

Problem Description

As the new term comes, the Ignatius Train Station is very busy nowadays. A lot of student want to get back to school by train(because the trains in the Ignatius Train Station is the fastest all over the world ^v^). But here comes a problem, there is only one railway where all the trains stop. So all the trains come in from one side and get out from the other side. For this problem, if train A gets into the railway first, and then train B gets into the railway before train A leaves, train A can't leave until train B leaves. The pictures below figure out the problem. Now the problem for you is, there are at most 9 trains in the station, all the trains has an ID(numbered from 1 to n), the trains get into the railway in an order O1, your task is to determine whether the trains can get out in an order O2.
![img](http://acm.hdu.edu.cn/data/images/1022-1.jpg)![img](http://acm.hdu.edu.cn/data/images/1022-2.jpg)![img](http://acm.hdu.edu.cn/data/images/1022-3.jpg)

 



Input

The input contains several test cases. Each test case consists of an integer, the number of trains, and two strings, the order of the trains come in:O1, and the order of the trains leave:O2. The input is terminated by the end of file. More details in the Sample Input.

 



Output

The output contains a string "No." if you can't exchange O2 to O1, or you should output a line contains "Yes.", and then output your way in exchanging the order(you should output "in" for a train getting into the railway, and "out" for a train getting out of the railway). Print a line contains "FINISH" after each test case. More details in the Sample Output.

 



Sample Input

```
3 123 321
3 123 312
```

 



Sample Output

```
Yes.
in
in
in
out
out
out
FINISH
No.
FINISH

HintHint 
For the first Sample Input, we let train 1 get in, then train 2 and train 3.
So now train 3 is at the top of the railway, so train 3 can leave first, then train 2 and train 1.
In the second Sample input, we should let train 3 leave first, so we have to let train 1 get in, then train 2 and train 3.
Now we can let train 3 leave.
But after that we can't let train 1 leave before train 2, because train 2 is at the top of the railway at the moment.
So we output "No.".
```

 



Author

Ignatius.L

 



Recommend

We have carefully selected several similar problems for you:  [1026](http://acm.hdu.edu.cn/showproblem.php?pid=1026) [1023](http://acm.hdu.edu.cn/showproblem.php?pid=1023) [1032](http://acm.hdu.edu.cn/showproblem.php?pid=1032) [2063](http://acm.hdu.edu.cn/showproblem.php?pid=2063) [1087](http://acm.hdu.edu.cn/showproblem.php?pid=1087) 

 



Accepted Code

```java
//经典栈
package cn.edu.hdu.acm;

import java.util.Scanner;
import java.util.Stack;
 
public class Main1022 {
	public static void main(String[] args){
		Scanner sc = new Scanner(System.in);
		while(sc.hasNext()){
			int n = sc.nextInt();
			int input = sc.nextInt();
			int output = sc.nextInt();
			input=rev(input);
			output = rev(output);
			Stack<Integer> in = new Stack<Integer>();
			Stack<Integer> out = new Stack<Integer>();
			Stack<String> sign = new Stack<String>();
			while(output!=0){
				int temp = output%10;
				out.add(0,temp);
				output /= 10;
			}
			while(input!=0){
				int temp = input%10;
				in.push(temp);
				sign.add(0,"in");
				input /= 10;
				while(!in.isEmpty()&&in.peek()==out.peek()){
					in.pop();
					out.pop();
					sign.add(0,"out");
				}
			}
			if(out.isEmpty()){
				System.out.println("Yes.");
				while(!sign.isEmpty()){
					System.out.println(sign.pop());
				}
			}else 
				System.out.println("No.");
			System.out.println("FINISH");
		}
	}
 
	private static int rev(int x) {
		String s = String.valueOf(x);
		String ss = new StringBuilder(s).reverse().toString();
		return Integer.parseInt(ss);
	}
}

```

