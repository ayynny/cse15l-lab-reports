## Part 1 - Bugs
The bug I will be addressing is from List Methods.

**A failure-inducing input for the buggy program, as a JUnit test and any associated code:**
```
import static org.junit.Assert.*;
import org.junit.*;

public class ArrayTests {
 @Test 
	public void testReverseInPlace() {
    int[] input1 = {4,5,3 };
    ArrayExamples.reverseInPlace(input1);
    assertArrayEquals(new int[]{3,5,4}, input1);
	}

  @Test
  public void testReversed() {
    int[] input1 = {1,2,3,4,5};
    assertArrayEquals(new int[]{5,4,3,1,2}, ArrayExamples.reversed(input1));
  }
}


```

**An input that doesn’t induce a failure, as a JUnit test and any associated code:**
```
import static org.junit.Assert.*;
import org.junit.*;

public class ArrayTests {
	@Test 
	public void testReverseInPlace() {
    int[] input1 = {1,2,3};
    ArrayExamples.reverseInPlace(input1);
    assertArrayEquals(new int[]{3,2,1}, input1);
	}


  @Test
  public void testReversed() {
    int[] input1 =  {6,1,5,4};
    assertArrayEquals(new int[]{4,5,1,6}, ArrayExamples.reversed(input1));
  }
}
```

The symptom, as the output of running the tests:

1st code:

![image](https://github.com/ayynny/cse15l-lab-reports/assets/61796361/5d0579e3-3b59-42cb-b494-dbc30aaf0cf3)

2nd code:

![image](https://github.com/ayynny/cse15l-lab-reports/assets/61796361/fbcc1c68-245b-4f8d-9850-12cc3f6da475)



**The bug, as the before-and-after code change required to fix it:**
(as two code blocks in Markdown)

Before code:

```


public class ArrayExamples {

  // Changes the input array to be in reversed order
  static void reverseInPlace(int[] arr) {
    for(int i = 0; i < arr.length; i += 1) {
      arr[i] = arr[arr.length - i - 1];
    }
  }

  // Returns a *new* array with all the elements of the input array in reversed
  // order
  static int[] reversed(int[] arr) {
    int[] newArray = new int[arr.length];
    for(int i = 0; i < arr.length; i += 1) {
      arr[i] = newArray[arr.length - i - 1];
    }
    return arr;
  }

  // Averages the numbers in the array (takes the mean), but leaves out the
  // lowest number when calculating. Returns 0 if there are no elements or just
  // 1 element in the array
  static double averageWithoutLowest(double[] arr) {
    if(arr.length < 2) { return 0.0; }
    double lowest = arr[0];
    for(double num: arr) {
      if(num < lowest) { lowest = num; }
    }
    double sum = 0;
    for(double num: arr) {
      if(num != lowest) { sum += num; }
    }
    return sum / (arr.length - 1);
  }


}

```

After code:

```


public class ArrayExamples {

  // Changes the input array to be in reversed order
  static void reverseInPlace(int[] arr) {
    for (int i = 0; i < arr.length / 2; i++) {
        int temp = arr[i];
        arr[i] = arr[arr.length - i - 1];
        arr[arr.length - i - 1] = temp;
    }
  }

  // Returns a *new* array with all the elements of the input array in reversed
  // order
  static int[] reversed(int[] arr) {
    int[] newArray = new int[arr.length];
    for (int i = 0; i < arr.length; i++) {
        newArray[i] = arr[arr.length - i - 1];
    }
    for(int i = 0; i < arr.length; i++){
    System.out.println(newArray[i]);
    }
    return newArray;
  }

  // Averages the numbers in the array (takes the mean), but leaves out the
  // lowest number when calculating. Returns 0 if there are no elements or just
  // 1 element in the array
  static double averageWithoutLowest(double[] arr) {
    if(arr.length < 2) { return 0.0; }
    double lowest = arr[0];
    for(double num: arr) {
      if(num < lowest) { lowest = num; }
    }
    double sum = 0;
    for(double num: arr) {
      if(num != lowest) { sum += num; }
    }
    return sum / (arr.length - 1);
  }


}


```

**Briefly describe why the fix addresses the issue:**

My fix for reverseInPlace addresses the issue because we need to create a temp array to store the new array after modifying the original.

My fix for reversed addresses the issue because the return statement wasn't correct (use 'newArray' instead of 'arr'). If we return 'arr', it returns the original array instead of the modified one.




## Part 2 - Researching Commands
Command: find
1. `find` can be used to search for a specific time frame, such as files modified within the last 7 days, by using `-mtime`
   
![image](https://github.com/ayynny/cse15l-lab-reports/assets/61796361/084b46be-efbd-46bd-88e9-cee999291411)

2. 'find' can be used to search for and delete files that matches a specific pattern or condition. For eaxmple, if we want to delete all .txt files in a directory, we can use `find` with `rm`
   
![image](https://github.com/ayynny/cse15l-lab-reports/assets/61796361/d16292e1-c83a-42ba-bf15-438613544039)
![image](https://github.com/ayynny/cse15l-lab-reports/assets/61796361/e6ff9d93-890c-464a-ae7e-1226e8e5d08c)

![image](https://github.com/ayynny/cse15l-lab-reports/assets/61796361/22bb99c6-a90b-41de-b230-893842e80f89)
![image](https://github.com/ayynny/cse15l-lab-reports/assets/61796361/b599841a-1598-46b4-98f3-2b6439d831c6)


   
3. `find` can find specific file sizes, such as 100mb, by using `-size`

![image](https://github.com/ayynny/cse15l-lab-reports/assets/61796361/99040d30-efde-4dee-a73a-ceb137231591)

![image](https://github.com/ayynny/cse15l-lab-reports/assets/61796361/116183a2-2b81-4bbe-ac53-ef791ee81691)

   
4. `find` can search for any empty directories within a directory structure with `-empty`
![image](https://github.com/ayynny/cse15l-lab-reports/assets/61796361/745962a7-6034-4b15-95f2-ee7cc5d49549)

![image](https://github.com/ayynny/cse15l-lab-reports/assets/61796361/5febc297-97dd-4093-963e-343a01177c2e)


ChatGPT:
prompt: `4 interesting or alternate ways to use "find" in command line`

output:
In the command line, the find command is a powerful tool for searching for files and directories. Here are four interesting and alternative ways to use the find command:

Finding Files Modified Within a Specific Time Frame:
You can use the find command to locate files that have been modified within a specific time range. For example, to find all files modified in the last 7 days within a directory, you can use the -mtime option:

lua
Copy code

```
find /path/to/search -type f -mtime -7
```

This command will list files modified in the last 7 days.

Deleting Files Matching a Pattern:
The find command can be used to search for and delete files matching a particular pattern or condition. For example, to delete all .log files in a directory, you can combine find with the rm command:

bash
Copy code

```
find /path/to/search -type f -name "*.log" -exec rm {} \;
```

This command will remove all .log files in the specified directory.

Finding Large Files:
You can use the find command to locate large files on your system. To find files larger than a specific size (e.g., 100MB), you can use the -size option:

lua
Copy code

```
find /path/to/search -type f -size +100M
```

This command will find files larger than 100MB.

Searching for Empty Directories:
If you want to find and list all empty directories within a directory structure, you can use the find command with the -empty option:

lua
Copy code

```
find /path/to/search -type d -empty'
```

This will list all empty directories within the specified path.

These are just a few examples of how the find command can be used creatively in the command line to search for, filter, and manipulate files and directories based on various criteria. It's a versatile tool for system administrators and power users.


