# Lab 3 Report 

## Part 1 - Bugs

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

## Part 2 - Researching Commands

### Option 2: Find (finding all directories) 

#### Example 1: ```find ./cse15l-lab-reports -type d```

This finds all the directories in the cse15l folder: 

```
./cse15l-lab-reports
./cse15l-lab-reports/.git
./cse15l-lab-reports/.git/objects
./cse15l-lab-reports/.git/objects/pack
./cse15l-lab-reports/.git/objects/info
./cse15l-lab-reports/.git/info
./cse15l-lab-reports/.git/logs
./cse15l-lab-reports/.git/logs/refs
./cse15l-lab-reports/.git/logs/refs/heads
./cse15l-lab-reports/.git/logs/refs/remotes
./cse15l-lab-reports/.git/logs/refs/remotes/origin
./cse15l-lab-reports/.git/hooks
./cse15l-lab-reports/.git/refs
./cse15l-lab-reports/.git/refs/heads
./cse15l-lab-reports/.git/refs/tags
./cse15l-lab-reports/.git/refs/remotes
./cse15l-lab-reports/.git/refs/remotes/origin
```

#### Example 2: ```find ./cse15l-lab-reports -type f -name "*.py"```

This finds all python files in the ```cse15l-lab-reports``` folder: 



