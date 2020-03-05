# FatMouse' Trade

**Time Limit: 2000/1000 MS (Java/Others)    Memory Limit: 65536/32768 K (Java/Others)Total Submission(s): 110592    Accepted Submission(s): 38140**

Problem Description

FatMouse prepared M pounds of cat food, ready to trade with the cats guarding the warehouse containing his favorite food, JavaBean.
The warehouse has N rooms. The i-th room contains J[i] pounds of JavaBeans and requires F[i] pounds of cat food. FatMouse does not have to trade for all the JavaBeans in the room, instead, he may get J[i]* a% pounds of JavaBeans if he pays F[i]* a% pounds of cat food. Here a is a real number. Now he is assigning this homework to you: tell him the maximum amount of JavaBeans he can obtain.

 



Input

The input consists of multiple test cases. Each test case begins with a line containing two non-negative integers M and N. Then N lines follow, each contains two non-negative integers J[i] and F[i] respectively. The last test case is followed by two -1's. All integers are not greater than 1000.

 



Output

For each test case, print in a single line a real number accurate up to 3 decimal places, which is the maximum amount of JavaBeans that FatMouse can obtain.

 



Sample Input

```
5 3
7 2
4 3
5 2
20 3
25 18
24 15
15 10
-1 -1
```

 



Sample Output

```
13.333
31.500
```

 



Author

CHEN, Yue

 



Source

[ZJCPC2004](http://acm.hdu.edu.cn/search.php?field=problem&key=ZJCPC2004&source=1&searchmode=source)

 



Recommend

JGShining   |   We have carefully selected several similar problems for you:  [1050](http://acm.hdu.edu.cn/showproblem.php?pid=1050) [1051](http://acm.hdu.edu.cn/showproblem.php?pid=1051) [2037](http://acm.hdu.edu.cn/showproblem.php?pid=2037) [1052](http://acm.hdu.edu.cn/showproblem.php?pid=1052) [1010](http://acm.hdu.edu.cn/showproblem.php?pid=1010) 





Accepted Code

```java
//贪心算法，数组实现
package cn.edu.hdu.acm;

import java.util.*;
import java.io.*;


/**
*数组实现，实现当中运用了快排，具体见static方法
*/
public class Main1009 {

    public static void main(String[] arg){
        Scanner scan = new Scanner(new BufferedInputStream(System.in));
        int m,n;
        while((m=scan.nextInt())!=-1&&(n=scan.nextInt())!=-1){
            double f[] = new double[n];//鼠食
            double j[] = new double[n];//猫粮
            double a[] = new double[n];
            double maxF=0;
            for(int i =0 ; i != n ; i ++){
                f[i] = scan.nextDouble();
                j[i] = scan.nextDouble();
                a[i] = f[i]/j[i];
            }
            sort(a,f,j);
            for(int i =n-1 ; i !=-1 ; i -- ){
                if(m>=j[i]){//这里必须打等于号  不然会导致结果不准确  ACM会WA
                    m -= j[i];
                    maxF += f[i];
                }else{
                    maxF += m*a[i];
                    break;
                }
            }
            System.out.printf("%.3f",maxF);
            System.out.println();
        }
        scan.close();
    }
    
    static void sort(double[] a,double[] b,double[] c) {
        int len = a.length;
        int low = 0,high = len - 1;
        quickSort(a,b,c, low, high);
    }

    static void quickSort(double[] a,double[] b, double[] c,int l ,int h){
        if(l>=h){
            return;
        }
        int low = l;
        int high = h;
        double k = a[low];
        double k2 = b[low];
        double k3 = c[low];
        while(low< high){
            //
            while(high>low&&a[high]>=k){//寻找元素右边比其小的
                high --;
            }
            a[low] = a[high];//进行交换，K指向high
            b[low] = b[high];
            c[low] = c[high];
            while(low<high&&a[low]<=k){//寻找元素左边比其大的
                low++;
            }
            a[high] = a[low];//进行交换，K指向low
            b[high] = b[low];
            c[high] = c[low];
        }
        a[low] = k;//将K赋给low
        b[low] = k2;
        c[low] = k3;
        quickSort(a,b, c,l, low-1);
        quickSort(a,b, c,low+1, h);
    }

}

```



```java
//贪心算法，OOP封装实现
package cn.edu.hdu.acm;

import java.util.*;
import java.io.*;

public class Main1009 {

    public static void main(String[] arg){
        Scanner scan = new Scanner(new BufferedInputStream(System.in));
        int m,n;
        while((m=scan.nextInt())!=-1&&(n=scan.nextInt())!=-1){
            ArrayList<Trade> trades = new ArrayList<>(n);
            double maxF=0;
            for(int i =0 ; i != n ; i ++){
                Trade trade = new Trade();
                trade.setF(scan.nextDouble());
                trade.setJ(scan.nextDouble());
                trades.add(trade);
            }
            Collections.sort(trades);
            for(int i =0 ; i !=n ; i ++ ){
                Trade trade = trades.get(i);
                if(m>= trade.getJ() ){
                    m -= trade.getJ() ;
                    maxF += trade.getF() ;
                }else{
                    maxF += m*trade.getA();
                    break;
                }
            }
            System.out.printf("%.3f",maxF);
            System.out.println();
        }
        scan.close();
    }
    
    static class Trade implements Comparable<Trade> {
        private double f;//鼠食
        private double j;//猫粮

        @Override
        public int compareTo(Trade o) {
            if(getA()>o.getA()){
                return -1;
            }else if(getA()==o.getA()){
                return 0;
            }
            return 1;
        }
        
        public double getF() {
            return f;
        }

        public void setF(double f) {
            this.f = f;
        }

        public double getJ() {
            return j;
        }

        public void setJ(double j) {
            this.j = j;
        }

        public double getA() {//获取性价比
            return f/j;
        }

    }

}

```

