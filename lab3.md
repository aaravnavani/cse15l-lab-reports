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
  
#### Example 1: ```find ./technical -type d```

This is the output of the command: 
```
./technical
./technical/government
./technical/government/About_LSC
./technical/government/Env_Prot_Agen
./technical/government/Alcohol_Problems
./technical/government/Gen_Account_Office
./technical/government/Post_Rate_Comm
./technical/government/Media
./technical/plos
./technical/biomed
./technical/911report
```

This lists out all directories that are in the technical folder. 


#### Example 2: ```find ./technical/911report -type f -name "*.txt"```

This finds all txt files in the ```cse15l-lab-reports``` folder: 

```
./technical/911report/chapter-13.4.txt
./technical/911report/chapter-13.5.txt
./technical/911report/chapter-13.1.txt
./technical/911report/chapter-13.2.txt
./technical/911report/chapter-13.3.txt
./technical/911report/chapter-3.txt
./technical/911report/chapter-2.txt
./technical/911report/chapter-1.txt
./technical/911report/chapter-5.txt
./technical/911report/chapter-6.txt
./technical/911report/chapter-7.txt
./technical/911report/chapter-9.txt
./technical/911report/chapter-8.txt
./technical/911report/preface.txt
./technical/911report/chapter-12.txt
./technical/911report/chapter-10.txt
./technical/911report/chapter-11.txt
```

This finds all the text files (of type `.txt`) in the `/technical/` directory. 

### Example 3: ```find ./technical -type f -name "*.txt" -exec rm {} \;```

This command finds all .txt files in the `/technical` folder and deletes them (using the `rm` command). When I go into the `/technical/911report/` there are no `.txt` files. 

### Example 4: ```find ./technical -type d -exec chmod 755 {} \;```

This command finds all directiories in the `/.technical` directory and sets their permissions to 755, which means that the owner can read, write, and edit but others can 
read and execute. 




