# Part 1 - Debugging Scenario
## Post from a Student:

**54 minutes ago in Lab**

> Hello, I am not sure why I am recieving junit test errors for my Lab 3. I am trying to run my ArrayTests, but I keep recieving this error and I can't run any tests. I believe the bug may be coming from the test script since that is where the junit is contained.

![image](https://github.com/ayynny/cse15l-lab-reports/assets/61796361/cd3602dd-0aa2-4002-881f-af70e15686e6)


## Response from a TA:

**Just Now**
> Hi there, depending on your operating system, then the classpath seperator may be incorrect. If you are on Windows, then the classpath seperator should be a semicolon instead of a colon. In addition, notice the syntax of previous bash scripts.
## Student's work after posting on EdStem

Hello, I think I figured it out. I needed to put quotes around the ```.;lib/hamcrest-core-1.3.jar;lib/junit-4.13.2.jar``` for the line to run the code, and change the colon to a semicolon. I think it is necessary to put the quotes because it creates a single string that represents the classpath argument to pass to ```java```. Thank you!

![image](https://github.com/ayynny/cse15l-lab-reports/assets/61796361/0d8f5b2e-7150-42c4-9da6-f771522b1f7d)


## Information about Setup

**File/Directory Structure:**

We should be in the lab3 folder. The necessary files for this set up are:

- Lab 3 (folder)
  - lib (folder)
  - ArrayExamples.class
  - ArrayExamples.java
  - ArrayTests.class
  - ArrayTests.java
  - test.sh
 
  The path that I am in to access necessary files is ```~/OneDrive/Documents/GitHub/lab3 ```

**Contents of files before fixing the bug:**

test.sh
```
set -e
javac -cp ".;lib/hamcrest-core-1.3.jar;lib/junit-4.13.2.jar" *.java
java -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar org.junit.runner.JUnitCore ArrayTests
```

**Command line I ran to trigger the bug:**

```
bash test.sh
```

**Edit to fix the bug:**

In the test.sh file, we needed to replace the colon with a semicolon because I am working on a Windows computer. If I were on a Mac or Linux OS, the colon could have been kept there, but the line to compile the code would also have to be a colon. In addition, quotes are needed to be wrapped around ```".;lib/hamcrest-core-1.3.jar;lib/junit-4.13.2.jar"``` to 
encapsulate the entire class path.

# Part 2 - Reflection

In the second half of the quarter, I didn't know that vim was a thing. I thought it was so, so cool that you could edit files completely remotely, and you don't even need an IDE to make your code run! Although vim was a bit of a learning curve, I was able to grasp it really quickly and it's definitely a shortcut to edit your files when you can just navigate through the terminal to find the file you want to edit. 
