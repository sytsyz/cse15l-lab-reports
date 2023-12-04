## Lab Report 5
1. Original Post \
    Hi: \
   I am trying to finish the lab for the auto grading/grader review. And I get this error message
```
   There was 1 failure:
1) initializationError(org.junit.runner.JUnitCommandLineParseResult)
java.lang.IllegalArgumentException: Could not find class [TestListExamples]
        at org.junit.runner.JUnitCommandLineParseResult.parseParameters(JUnitCommandLineParseResult.java:100)
        at org.junit.runner.JUnitCommandLineParseResult.parseArgs(JUnitCommandLineParseResult.java:50)
        at org.junit.runner.JUnitCommandLineParseResult.parse(JUnitCommandLineParseResult.java:44)
        at org.junit.runner.JUnitCore.runMain(JUnitCore.java:72)
        at org.junit.runner.JUnitCore.main(JUnitCore.java:36)
Caused by: java.lang.ClassNotFoundException: TestListExamples
        at java.base/jdk.internal.loader.BuiltinClassLoader.loadClass(BuiltinClassLoader.java:581)
        at java.base/jdk.internal.loader.ClassLoaders$AppClassLoader.loadClass(ClassLoaders.java:178)
        at java.base/java.lang.ClassLoader.loadClass(ClassLoader.java:521)
        at java.base/java.lang.Class.forName0(Native Method)
        at java.base/java.lang.Class.forName(Class.java:398)
        at org.junit.internal.Classes.getClass(Classes.java:42)
        at org.junit.internal.Classes.getClass(Classes.java:27)
        at org.junit.runner.JUnitCommandLineParseResult.parseParameters(JUnitCommandLineParseResult.java:98)
        ... 4 more

FAILURES!!!
Tests run: 1,  Failures: 1
```
I can clone and complie correctly, just not the final grading? Here is a screenshot of my code, please help me!!
> <img width="1493" alt="image" src="https://github.com/sytsyz/cse15l-lab-reports/assets/146896888/3eb7364e-a4d6-484b-9131-7325c9611678">

2. TA Response\
   Hi: \
   By looking at your code, it looks like it's a pathway error. You might want to check the java and javac command to see if you have nevigated to the correct place. (line 25 and 30)
   Hint: your program might not be able to locate your starting point.

3. Student Trying \
   after change: \
   25
   ```
   javac -cp .:../lib/hamcrest-core-1.3.jar:../lib/junit-4.13.2.jar *.java
   ```
   30:
   ```
   java -cp .:../lib/hamcrest-core-1.3.jar:../lib/junit-4.13.2.jar org.junit.runner.JUnitCore TestListExamples > output.txt
   ```
   terminal:
   ```
   % bash grade.sh https://github.com/ucsd-cse15l-f22/list-methods-corrected
   Cloning into 'student-submission'...
   remote: Enumerating objects: 3, done.
   remote: Counting objects: 100% (3/3), done.
   remote: Compressing objects: 100% (2/2), done.
   remote: Total 3 (delta 0), reused 3 (delta 0), pack-reused 0
   Receiving objects: 100% (3/3), done.
   Finished cloning
   it works
   complied successfully
   /Users/linda/Documents/GitHub/newweek4/grader-review-sytsyz/grading-area
   JUnit version 4.13.2
   .
   Time: 0.02

   OK (1 test)
   ```
   The error was: the missing .: at the beginning of the path. Need to provide the full relative path to the desitnation, starting with . to indicate start at currrent working directory. The program does not automatically consider things located in the current directory.

   4. Summarize;
      The file & directory structure needed: \
      > <img width="330" alt="image" src="https://github.com/sytsyz/cse15l-lab-reports/assets/146896888/ce58cf1c-0ce2-44cf-bfd8-695913b191e1">
      
      The contents of each file before fixing the bug:\
      > <img width="751" alt="image" src="https://github.com/sytsyz/cse15l-lab-reports/assets/146896888/e521557b-26f8-42f6-857b-e13e575271bd">
      > <img width="654" alt="image" src="https://github.com/sytsyz/cse15l-lab-reports/assets/146896888/1639c622-a356-47c3-8df2-559661252c59">
      > <img width="782" alt="image" src="https://github.com/sytsyz/cse15l-lab-reports/assets/146896888/c2b8928c-a441-4f0b-a727-5b75df3aa1c4">
      > <img width="1042" alt="image" src="https://github.com/sytsyz/cse15l-lab-reports/assets/146896888/310b1ef6-1788-48d5-8e0f-922124651c05">
      > <img width="1005" alt="image" src="https://github.com/sytsyz/cse15l-lab-reports/assets/146896888/b64a898d-6498-4a28-9ee7-57526045484f">
      <img width="942" alt="image" src="https://github.com/sytsyz/cse15l-lab-reports/assets/146896888/1d49023a-4fbc-4fe5-a1f5-ce816060a490">
      > <img width="919" alt="image" src="https://github.com/sytsyz/cse15l-lab-reports/assets/146896888/33b953e0-0b48-4de5-9234-c22dd51dc28c">
      > <img width="719" alt="image" src="https://github.com/sytsyz/cse15l-lab-reports/assets/146896888/c0897f72-3f64-4624-9e9d-db23abee5e1e">

      The contents of each files after fixing the bugs: \
      everything remians the same except for grade.sh
      >
      

      
  
      


      

      





   


