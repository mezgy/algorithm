# Ignatius and the Princess II

**Time Limit: 2000/1000 MS (Java/Others)    Memory Limit: 65536/32768 K (Java/Others)Total Submission(s): 13475    Accepted Submission(s): 7754**

Problem Description

Now our hero finds the door to the BEelzebub feng5166. He opens the door and finds feng5166 is about to kill our pretty Princess. But now the BEelzebub has to beat our hero first. feng5166 says, "I have three question for you, if you can work them out, I will release the Princess, or you will be my dinner, too." Ignatius says confidently, "OK, at last, I will save the Princess."

"Now I will show you the first problem." feng5166 says, "Given a sequence of number 1 to N, we define that 1,2,3...N-1,N is the smallest sequence among all the sequence which can be composed with number 1 to N(each number can be and should be use only once in this problem). So it's easy to see the second smallest sequence is 1,2,3...N,N-1. Now I will give you two numbers, N and M. You should tell me the Mth smallest sequence which is composed with number 1 to N. It's easy, isn't is? Hahahahaha......"
Can you help Ignatius to solve this problem?

 



Input

The input contains several test cases. Each test case consists of two numbers, N and M(1<=N<=1000, 1<=M<=10000). You may assume that there is always a sequence satisfied the BEelzebub's demand. The input is terminated by the end of file.

 



Output

For each test case, you only have to output the sequence satisfied the BEelzebub's demand. When output a sequence, you should print a space between two numbers, but do not output any spaces after the last number.

 



Sample Input

```
6 4
11 8
```

 



Sample Output

```
1 2 3 5 6 4
1 2 3 4 5 6 7 9 8 11 10
```

 



Author

Ignatius.L

 



Recommend

We have carefully selected several similar problems for you:  [1038](http://acm.hdu.edu.cn/showproblem.php?pid=1038) [1029](http://acm.hdu.edu.cn/showproblem.php?pid=1029) [1035](http://acm.hdu.edu.cn/showproblem.php?pid=1035) [1030](http://acm.hdu.edu.cn/showproblem.php?pid=1030) [1028](http://acm.hdu.edu.cn/showproblem.php?pid=1028) 





Accepted Code

```java
package cn.edu.hdu.acm;

import java.util.*;

public class Main1027 {
	public static void main(String[] args) {
		Scanner in = new Scanner(System.in);
		while (in.hasNext()) {
			int N = in.nextInt();
			int M = in.nextInt();
			int[] a = new int[N];
			for (int i = 0; i < a.length; i++) 
				a[i] = i + 1;
			for (int i = 1; i < M; i++)
				nextPermutation(a);
			System.out.print(a[0]);
			for (int i = 1; i < a.length; i++)
				System.out.print(" " + a[i]);
			System.out.println();
		}
	}
 
	public static void nextPermutation(int[] a) {
		int llr = 0;
		for (int i = a.length - 1; i > 0; i--)
			if (a[i - 1] < a[i]) {
				llr = i - 1;
				break;
			}
 
		int min = llr + 1;
		for (int i = llr + 1; i < a.length; i++)
			if (a[i] > a[llr] && a[i] < a[min])
				min = i;
 
		swap(llr, min, a);
		reserve(llr + 1, a);
	}
 
	public static void swap(int i, int j, int[] a) {
		int temp = a[i];
		a[i] = a[j];
		a[j] = temp;
	}
 
	public static void reserve(int i, int[] a) {
		for (int j = i, k = 0; j < (i + a.length) / 2; j++, k++) 
			swap(j, a.length - 1 - k, a);
	}
}
```

