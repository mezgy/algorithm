# Keep on Truckin'

**Time Limit: 2000/1000 MS (Java/Others)    Memory Limit: 65536/32768 K (Java/Others)Total Submission(s): 19860    Accepted Submission(s): 13406**

Problem Description

Boudreaux and Thibodeaux are on the road again . . .

"Boudreaux, we have to get this shipment of mudbugs to Baton Rouge by tonight!"

"Don't worry, Thibodeaux, I already checked ahead. There are three underpasses and our 18-wheeler will fit through all of them, so just keep that motor running!"

"We're not going to make it, I say!"

So, which is it: will there be a very messy accident on Interstate 10, or is Thibodeaux just letting the sound of his own wheels drive him crazy?

 



Input

Input to this problem will consist of a single data set. The data set will be formatted according to the following description.

The data set will consist of a single line containing 3 numbers, separated by single spaces. Each number represents the height of a single underpass in inches. Each number will be between 0 and 300 inclusive.

 



Output

There will be exactly one line of output. This line will be:

   NO CRASH

if the height of the 18-wheeler is less than the height of each of the underpasses, or:

   CRASH X

otherwise, where X is the height of the first underpass in the data set that the 18-wheeler is unable to go under (which means its height is less than or equal to the height of the 18-wheeler).
The height of the 18-wheeler is 168 inches.

 



Sample Input

```
180 160 170
```

 



Sample Output

```
CRASH 160
```

 



Source

[South Central USA 2003](http://acm.hdu.edu.cn/search.php?field=problem&key=South+Central+USA+2003&source=1&searchmode=source)

 



Recommend

We have carefully selected several similar problems for you:  [1040](http://acm.hdu.edu.cn/showproblem.php?pid=1040) [1064](http://acm.hdu.edu.cn/showproblem.php?pid=1064) [1038](http://acm.hdu.edu.cn/showproblem.php?pid=1038) [1056](http://acm.hdu.edu.cn/showproblem.php?pid=1056) [1048](http://acm.hdu.edu.cn/showproblem.php?pid=1048) 





Accepted Code

```java
package cn.edu.hdu.acm;

import java.util.Scanner;

public class Main1037 {
    private static Scanner scanner;

    public static void main(String[] args) {
        scanner = new Scanner(System.in);
        while(scanner.hasNext()){
            double arr[] = new double[3];
            boolean isCrash = false;
            for (int i = 0; i < 3; i++) {
                arr[i] = scanner.nextDouble();
                if(arr[i]<168){
                    isCrash = true;
                    System.out.println("CRASH "+(int)arr[i]);
                }
            }
            if(!isCrash){
                System.out.println("NO CRASH");
            }
        }
    }
}

```

