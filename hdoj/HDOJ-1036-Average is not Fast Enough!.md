# Average is not Fast Enough!

**Time Limit: 2000/1000 MS (Java/Others)    Memory Limit: 65536/32768 K (Java/Others)Total Submission(s): 7645    Accepted Submission(s): 3218**

Problem Description

A relay is a race for two or more teams of runners. Each member of a team runs one section of the race. Your task is to help to evaluate the results of a relay race.

You have to process several teams. For each team you are given a list with the running times for every section of the race. You are to compute the average time per kilometer over the whole distance. That's easy, isn't it?
So if you like the fun and challenge competing at this contest, perhaps you like a relay race, too. Students from Ulm participated e.g. at the "SOLA" relay in Zurich, Switzerland. For more information visit http://www.sola.asvz.ethz.ch/ after the contest is over.

 



Input

The first line of the input specifies the number of sections n followed by the total distance of the relay d in kilometers. You may safely assume that 1 <= n <= 20 and 0.0 < d < 200.0. Every following line gives information about one team: the team number t (an integer, right-justified in a field of width 3) is followed by the n results for each section, separated by a single space. These running times are given in the format "h:mm:ss" with integer numbers for the hours, minutes and seconds, respectively. In the special case of a runner being disqualified, the running time will be denoted by "-:--:--". Finally, the data on every line is terminated by a newline character. Input is terminated by EOF.

 



Output

For each team output exactly one line giving the team's number t right aligned in a field of width 3, and the average time for this team rounded to whole seconds in the format "m:ss". If at least one of the team's runners has been disqualified, output "-" instead. Adhere to the sample output for the exact format of presentation.

 



Sample Input

```
2 12.5
  5 0:23:21 0:25:01
 42 0:23:32 -:--:--
  7 0:33:20 0:41:35
```

 



Sample Output

```
  5: 3:52 min/km
 42: -
  7: 6:00 min/km
```

 



Source

[University of Ulm Local Contest 2001](http://acm.hdu.edu.cn/search.php?field=problem&key=University+of+Ulm+Local+Contest+2001&source=1&searchmode=source)

 



Recommend

We have carefully selected several similar problems for you:  [1039](http://acm.hdu.edu.cn/showproblem.php?pid=1039) [1037](http://acm.hdu.edu.cn/showproblem.php?pid=1037) [1038](http://acm.hdu.edu.cn/showproblem.php?pid=1038) [1048](http://acm.hdu.edu.cn/showproblem.php?pid=1048) [1062](http://acm.hdu.edu.cn/showproblem.php?pid=1062) 





Accepted Code

```java
package cn.edu.hdu.acm;

import java.util.ArrayList;
import java.util.List;
import java.util.Scanner;

public class Main1036 {

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        List<Team> list = new ArrayList<Team>();
        int n = sc.nextInt();
        double d = sc.nextDouble();
        while (sc.hasNext()) {
            Team t = new Team();
            t.id = sc.nextInt();
            t.times = new String[n];
            for (int i = 0; i < n; i++) {
                t.times[i] = sc.next();
            }
            list.add(t);
        }
        for (int i = 0; i < list.size(); i++) {
            Team t = list.get(i);
            System.out.printf("%3d: ", t.id);
            double time = 0;
            boolean yes = true;
            for (int j = 0; j < n; j++) {
                String str = t.times[j];
                String[] split = str.split(':' + "");
                try {
                    time += Integer.valueOf(split[0]) * 60 + Integer.valueOf(split[1])
                            + 1.0 * Integer.valueOf(split[2]) / 60;
                } catch (NumberFormatException e) {
                    yes = false;
                    break;
                }
            }
            if (!yes) {
                System.out.println("-");
                continue;
            }
            double ans = time / d;
            int m = 0;
            int s = 0;
            m = (int)ans;
            s = (int)((ans-m)*60+0.5);//四舍五入
            if (s>=60) {
                m++;
                s = s-60;
            }
            System.out.printf("%d:%02d min/km",m,s);
            System.out.println();
        }
        sc.close();
    }
}

class Team {
    int id;
    String times[];
}

```

