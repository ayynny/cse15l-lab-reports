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
