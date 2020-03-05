# Easier Done Than Said?

**Time Limit: 2000/1000 MS (Java/Others)    Memory Limit: 65536/32768 K (Java/Others)Total Submission(s): 18298    Accepted Submission(s): 8653**

Problem Description

Password security is a tricky thing. Users prefer simple passwords that are easy to remember (like buddy), but such passwords are often insecure. Some sites use random computer-generated passwords (like xvtpzyo), but users have a hard time remembering them and sometimes leave them written on notes stuck to their computer. One potential solution is to generate "pronounceable" passwords that are relatively secure but still easy to remember.

FnordCom is developing such a password generator. You work in the quality control department, and it's your job to test the generator and make sure that the passwords are acceptable. To be acceptable, a password must satisfy these three rules:

It must contain at least one vowel.

It cannot contain three consecutive vowels or three consecutive consonants.

It cannot contain two consecutive occurrences of the same letter, except for 'ee' or 'oo'.

(For the purposes of this problem, the vowels are 'a', 'e', 'i', 'o', and 'u'; all other letters are consonants.) Note that these rules are not perfect; there are many common/pronounceable words that are not acceptable.

 



Input

The input consists of one or more potential passwords, one per line, followed by a line containing only the word 'end' that signals the end of the file. Each password is at least one and at most twenty letters long and consists only of lowercase letters.

 



Output

For each password, output whether or not it is acceptable, using the precise format shown in the example.

 



Sample Input

```
a
tv
ptoui
bontres
zoggax
wiinq
eep
houctuh
end
```

 



Sample Output

```
<a> is acceptable.
<tv> is not acceptable.
<ptoui> is not acceptable.
<bontres> is not acceptable.
<zoggax> is not acceptable.
<wiinq> is not acceptable.
<eep> is acceptable.
<houctuh> is acceptable.
```

 



Source

[Mid-Central USA 2000](http://acm.hdu.edu.cn/search.php?field=problem&key=Mid-Central+USA+2000&source=1&searchmode=source)

 



Recommend

We have carefully selected several similar problems for you:  [1062](http://acm.hdu.edu.cn/showproblem.php?pid=1062) [1073](http://acm.hdu.edu.cn/showproblem.php?pid=1073) [1043](http://acm.hdu.edu.cn/showproblem.php?pid=1043) [1088](http://acm.hdu.edu.cn/showproblem.php?pid=1088) [1113](http://acm.hdu.edu.cn/showproblem.php?pid=1113) 





Accepted Code

```java
package cn.edu.hdu.acm;

import java.util.Scanner;

public class Main1039 {
    static char ch[] = { 'a', 'e', 'i', 'o', 'u' };

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        while (sc.hasNext()) {
            String str = sc.next();
            if ("end".equals(str)) {
                break;
            }
            boolean ans[] = new boolean[str.length()];
            boolean condition1 = false;
            boolean condition2 = true;
            boolean condition3 = true;
            for (int i = 0; i < str.length(); i++) {
                char c = str.charAt(i);
                if (isVowel(c)) {
                    ans[i] = true;
                    condition1 = true;
                }
                if (i > 0) {
                    char c2 = str.charAt(i - 1);
                    if (c != 'e' && c != 'o' && c2 == c) {
                        condition3 = false;
                        break;
                    }
                }
            }
            if (!condition3) {
                System.out.println("<" + str + "> is not acceptable.");
                continue;
            }
            if (!condition1) {
                System.out.println("<" + str + "> is not acceptable.");
                continue;
            }
            int x = 0;
            int y = 0;
            for (int i = 0; i < ans.length; i++) {
                if (ans[i]) {
                    y=0;
                    x++;
                }else{
                    x=0;
                    y++;
                }
                if (x==3||y==3) {
                    condition2 = false;
                    break;
                }
            }
            if (!condition2) {
                System.out.println("<" + str + "> is not acceptable.");
                continue;
            }
            System.out.println("<" + str + "> is acceptable.");
        }
        sc.close();
    }

    public static boolean isVowel(char c) {
        for (int i = 0; i < ch.length; i++) {
            if (c == ch[i]) {
                return true;
            }
        }
        return false;
    }
}

/*正则表达式解法*/
package cn.edu.hdu.acm;

import java.util.Scanner;
import java.util.regex.Matcher;
import java.util.regex.Pattern;
import static java.util.regex.Pattern.*;

public class Main1039 {

    public static void main(String[] args) throws Exception {
        Scanner cin = new Scanner(System.in);
        while (cin.hasNext()) {
            String str = cin.next();
            if(str.equals("end")){
                break;
            }
            Pattern p1 = compile("[aeiou]{3}|[^aeiou]{3}");
            Pattern p2 = compile("([^eo])\\1");
            Pattern p3 = compile("[aeiou]+");
            Matcher m = p1.matcher(str);
            boolean flag = false;
            if(!m.find())
            {
                m = p2.matcher(str);
                if(!m.find())
                {
                    m = p3.matcher(str);
                    if(m.find()) {
                        flag = true;
                    }
                }
            }
            if(flag) {
                System.out.println("<" + str + "> is acceptable.");
            }
            else {
                System.out.println("<" + str + "> is not acceptable.");
            }
        }
        cin.close();
    }
}
```

