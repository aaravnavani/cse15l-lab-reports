# Lab 3 Report 

## Part 1 

### A failure-inducing input for the buggy program, as a JUnit test and any associated code (write it as a code block in Markdown)

A failure-inducing input for this problem is the array: 

```@Test
  public void testReversed() {
    int[] input1 = { 1, 2, 3, 4 };
    assertArrayEquals(new int[]{ 4, 3, 2, 1 }, ArrayExamples.reversed(input1));
  }
```

Instead of returning the array [4, 3, 2, 1], it returns [0,0,0,0] and clears the array. 

### An input that doesn't induce a failure, as a JUnit test and any associated code (write it as a code block in Markdown)

An input that doesn't induce a failure is [0,0,0,0]: 

```@Test
  public void testReversed() {
    int[] input1 = { 0, 0, 0, 0 };
    assertArrayEquals(new int[]{ 0, 0, 0, 0 }, ArrayExamples.reversed(input1));
  }
```

It properly returns the reverse of [0,0,0,0] which is the array [0,0,0,0].

### The symptom, as the output of running the tests (provide it as a screenshot of running JUnit with at least the two inputs above)

The symptom is that the method clears the array instead of reversing it. 

### The bug, as the before-and-after code change required to fix it (as two code blocks in Markdown)

Old code: 

```static int[] reversed(int[] arr) {
    int[] newArray = new int[arr.length];
    for(int i = 0; i < arr.length; i += 1) {
      arr[i] = newArray[arr.length - i - 1];
    }
    return arr;
  }
```

Revised Code:

```
static int[] reversed(int[] arr) {
    int[] newArray = new int[arr.length];
    for(int i = 0; i < arr.length; i += 1) {
      newArray[i] = arr[arr.length - i - 1];
    }
    return newArray;
  }
```
