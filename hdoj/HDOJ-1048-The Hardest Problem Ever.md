# The Hardest Problem Ever

**Time Limit: 2000/1000 MS (Java/Others)    Memory Limit: 65536/32768 K (Java/Others)Total Submission(s): 35338    Accepted Submission(s): 16301**

Problem Description

Julius Caesar lived in a time of danger and intrigue. The hardest situation Caesar ever faced was keeping himself alive. In order for him to survive, he decided to create one of the first ciphers. This cipher was so incredibly sound, that no one could figure it out without knowing how it worked.
You are a sub captain of Caesar's army. It is your job to decipher the messages sent by Caesar and provide to your general. The code is simple. For each letter in a plaintext message, you shift it five places to the right to create the secure message (i.e., if the letter is 'A', the cipher text would be 'F'). Since you are creating plain text out of Caesar's messages, you will do the opposite:

Cipher text
A B C D E F G H I J K L M N O P Q R S T U V W X Y Z

Plain text
V W X Y Z A B C D E F G H I J K L M N O P Q R S T U

Only letters are shifted in this cipher. Any non-alphabetical character should remain the same, and all alphabetical characters will be upper case.

 



Input

Input to this problem will consist of a (non-empty) series of up to 100 data sets. Each data set will be formatted according to the following description, and there will be no blank lines separating data sets. All characters will be uppercase.

A single data set has 3 components:

Start line - A single line, "START"

Cipher message - A single line containing from one to two hundred characters, inclusive, comprising a single message from Caesar

End line - A single line, "END"

Following the final data set will be a single line, "ENDOFINPUT".

 



Output

For each data set, there will be exactly one line of output. This is the original message by Caesar.

 



Sample Input

```
START
NS BFW, JAJSYX TK NRUTWYFSHJ FWJ YMJ WJXZQY TK YWNANFQ HFZXJX
END
START
N BTZQI WFYMJW GJ KNWXY NS F QNYYQJ NGJWNFS ANQQFLJ YMFS XJHTSI NS WTRJ
END
START
IFSLJW PSTBX KZQQ BJQQ YMFY HFJXFW NX RTWJ IFSLJWTZX YMFS MJ
END
ENDOFINPUT
```

 



Sample Output

```
IN WAR, EVENTS OF IMPORTANCE ARE THE RESULT OF TRIVIAL CAUSES
I WOULD RATHER BE FIRST IN A LITTLE IBERIAN VILLAGE THAN SECOND IN ROME
DANGER KNOWS FULL WELL THAT CAESAR IS MORE DANGEROUS THAN HE
```

 



Source

[South Central USA 2002](http://acm.hdu.edu.cn/search.php?field=problem&key=South+Central+USA+2002&source=1&searchmode=source)

 



Recommend

We have carefully selected several similar problems for you:  [1062](http://acm.hdu.edu.cn/showproblem.php?pid=1062) [1091](http://acm.hdu.edu.cn/showproblem.php?pid=1091) [1076](http://acm.hdu.edu.cn/showproblem.php?pid=1076) [1092](http://acm.hdu.edu.cn/showproblem.php?pid=1092) [1095](http://acm.hdu.edu.cn/showproblem.php?pid=1095) 





Accepted Code

```java
package cn.edu.hdu.acm;

import java.util.Scanner;

public class Main1048 {
    private static Scanner scanner;

    public static void main(String[] args) {
        scanner = new Scanner(System.in);
        while (scanner.hasNext()) {
            String line = scanner.nextLine();
            //如果是START，END就不管他，如果是ENDOFINPUT就退出程序
            if(line.equals("START")||line.equals("END")){
                continue;
            }else if (line.equals("ENDOFINPUT")) {
                break;
            }
            char[] ch = line.toCharArray();
            for (int i = 0; i < ch.length; i++) {
                //如果不是A~Z不需要修改
                if (ch[i] >= 'A' && ch[i] <= 'Z') {
                    ch[i] -= 5;
                    //这是一个循环的过程
                    if (ch[i] < 'A') {
                        ch[i] += 26;
                    }
                }
            }
            for (char c : ch) {
                System.out.print(c);
            }
            System.out.println();
        }
    }
}

```

