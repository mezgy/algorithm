# Biker's Trip Odometer

**Time Limit: 2000/1000 MS (Java/Others)    Memory Limit: 65536/32768 K (Java/Others)Total Submission(s): 7549    Accepted Submission(s): 5002**

Problem Description

Most bicycle speedometers work by using a Hall Effect sensor fastened to the front fork of the bicycle. A magnet is attached to one of the spokes on the front wheel so that it will line up with the Hall Effect switch once per revolution of the wheel. The speedometer monitors the sensor to count wheel revolutions. If the diameter of the wheel is known, the distance traveled can be easily be calculated if you know how many revolutions the wheel has made. In addition, if the time it takes to complete the revolutions is known, the average speed can also be calculated.
For this problem, you will write a program to determine the total distance traveled (in miles) and the average speed (in Miles Per Hour) given the wheel diameter, the number of revolutions and the total time of the trip. You can assume that the front wheel never leaves the ground, and there is no slipping or skidding.

 



Input

Input consists of multiple datasets, one per line, of the form:

diameter revolutions time

The diameter is expressed in inches as a floating point value. The revolutions is an integer value. The time is expressed in seconds as a floating point value. Input ends when the value of revolutions is 0 (zero).

 



Output

For each data set, print:

Trip #N: distance MPH

Of course N should be replaced by the data set number, distance by the total distance in miles (accurate to 2 decimal places) and MPH by the speed in miles per hour (accurate to 2 decimal places). Your program should not generate any output for the ending case when revolutions is 0.

Constants

For p use the value: 3.1415927.
There are 5280 feet in a mile.
There are 12 inches in a foot.
There are 60 minutes in an hour.
There are 60 seconds in a minute.
There are 201.168 meters in a furlong.

 



Sample Input

```
26 1000 5
27.25 873234 3000
26 0 1000
```

 



Sample Output

```
Trip #1: 1.29 928.20
Trip #2: 1179.86 1415.84
```

 



Source

[Greater New York 2003](http://acm.hdu.edu.cn/search.php?field=problem&key=Greater+New+York+2003&source=1&searchmode=source)

 



Recommend

We have carefully selected several similar problems for you:  [1064](http://acm.hdu.edu.cn/showproblem.php?pid=1064) [1084](http://acm.hdu.edu.cn/showproblem.php?pid=1084) [1046](http://acm.hdu.edu.cn/showproblem.php?pid=1046) [1060](http://acm.hdu.edu.cn/showproblem.php?pid=1060) [1041](http://acm.hdu.edu.cn/showproblem.php?pid=1041) 

 





Accepted Code

```java
package cn.edu.hdu.acm;

import java.util.Scanner;

public class Main1038 {
    public static void main(String[] args) {
        Scanner in = new Scanner(System.in);
        int n = 0;
        while(in.hasNext()) {
            float diameter = (float) ((in.nextFloat() * 3.1415927)/(12*5280));
            int revolution = in.nextInt();
            if(revolution == 0) {
                break;
            }
            float time = in.nextFloat()/3600;
            float distance = diameter * revolution;
            float mph = distance / time;
            System.out.printf("Trip #%d: %.2f %.2f", ++n, distance, mph);
            System.out.println();
        }
    }
}
```

