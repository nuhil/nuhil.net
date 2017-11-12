+++
languageCode = "en-us"
title = "Understanding Big O notations - Algorithmic Efficiency"
author = "Nuhil Mehdy"
categories = ["Algorithm"]
tags = ["Big O", "Algorithm", "Complexity"]
date = "2016-03-01"
description = "Analysis of algorithms and making sense of algorithm complexity."
featured = ""
featuredalt = "Algorithm"
featuredpath = "//i.imgur.com/G8hyQZB.jpg"
linktitle = ""
type = "post"
+++

Well, if you are here by googling then I assume you already know what an Algorithm is. If not (somehow) then let me tell you what it means. An algorithm is a process or set of rules to be followed in calculations or other problem-solving operations, especially by a computer.

So, as per Computer Science context, to make a computer do anything, you have to write a computer program. To write a computer program, you have to tell the computer, step by step, exactly what you want it to do. The computer then "executes" the program, following each step mechanically, to accomplish the end goal. By mechanically it means, eventual machine code instructions the Computer Processor considers to do some basic operation like - input, output, math, conditional execution, repetition. Every program you’ve ever used, no matter how complicated, is made up of instructions that look more or less like these.

I have read and observed some contents from the internet to understand how the complexity of an Algorithm is determined and why its so important. I am writing this blog post about what I understood so far as one of my self notes and obviously for the readers if they find it useful.

Anyway, by determining the Big O notation of an algorithm we actually try to figure out how an specific algorithm scales as the amount of data involved in that operation increases. Its not for measuring the speed but for measuring the scalability of the computation based on different amount of handled data.

## O(1):

First of all, Lets look at the following Java program,
 
```java
import java.util.Arrays;

public class Main {
    private int[] theArray;
    private int arraySize;
    private int itemsInArray = 0;
    static long startTime;
    static long endTime;

    public static void main(String[] args) {
        Main BigOone = new Main(10000);
        BigOone.addItemToArray(314);

        System.out.println(Arrays.toString(BigOone.theArray));
    }

    Main(int size) {
        arraySize = size;
        theArray = new int[size];
    }

    public void addItemToArray(int itemToBeAdded) {
        theArray[itemsInArray] = itemToBeAdded;

    }
}
```

[Try it Online](http://ideone.com/VUGjBc)

Here we first initializing an integer Array with user defined size by the help of the class constructor. Later by the `method addItemToArray`, we are adding a new element (314 for example) to the first index of the initialized blank Array by calling this method from main method.
This is a simple program but has an algorithm too (to add elements to an Array). The most important instruction that has the impact on the performance of the algorithm is `theArray[itemsInArray] = itemToBeAdded;`. So, we have to inspect this instruction and decide whether this instruction is scalable for any amount of data or not.
Here, it does not matter how large an Array you are initializing. It will simply add a chosen element to its first index and its done. So, this algorithm will always take specific/constant amount of time (as per CPU) no matter how big the Array is. So, the complexity of this algorithm is O(1). 1 means constant in this context.

## O(n):

Now, think about a hard working algorithm which has to do more work based on the amount of input data to be manipulated. For example - *Linear Search in Array* is a job where you have to find a specific element into an Array for which your program or algorithm or steps need to check every elements of that array. So, if the subject Array is small then the program needs less operation and if the Array is very very large then the program needs longer operation that will increase time complexity and also space complexity in some scenario.
Lets see the following program,

```java
public class Main {
    private int[] theArray;
    private int arraySize;
    private int itemsInArray = 0;
    static long startTime;
    static long endTime;

    public static void main(String[] args) {
        Main testLinearSearchAlgo = new Main(1000);
        testLinearSearchAlgo.generateRandomArray();

        Main testLinearSearchAlgoAgain = new Main(9000);
        testLinearSearchAlgoAgain.generateRandomArray();

        testLinearSearchAlgo.linearSearch(20);
        testLinearSearchAlgoAgain.linearSearch(20);

    }

    Main(int size) {
        arraySize = size;
        theArray = new int[size];
    }

    public void linearSearch(int value) {

        boolean valueInArray = false;
        String indexsWithValue = &quot;&quot;;

        startTime = System.currentTimeMillis();

        for (int i = 0; i &lt; arraySize; i++) {

            if (theArray[i] == value) {
                valueInArray = true;
                indexsWithValue += i + &quot; &quot;;
            }

        }

        System.out.println(&quot;Value Found: &quot; + valueInArray);
        endTime = System.currentTimeMillis();
        System.out.println(&quot;Linear Search Took: &quot; + (endTime - startTime)
            +&quot;ms&quot;);
        System.out.println(&quot;In which Index: &quot; + indexsWithValue);

    }

    public void generateRandomArray() {

        for (int i = 0; i &lt; arraySize; i++) {
            theArray[i] = (int) (Math.random() * 1000) + 10;
        }

        itemsInArray = arraySize - 1;

    }
}
```

[Try it Online](http://ideone.com/RIFD7e)

Before analyzing the actual algorithm, let me clear out few things on the above program. First of all, we are taking help of a method called `generateRandomArray` which simply creates some random integer elements and put into the `theArray` array. After doing the insertion it defines the final array size also.

Anyway, as per our experiment (we want to search linearly) the actual searching happens on the `linearSearch` method. It takes only one argument as the value which to search on the array. Inside the body we did some very basic coding by which we are comparing every elements of the array with our chosen one. If at any stage, a match found then we are setting a flag `valueInArray` to True.
You may be already getting the idea about this algorithm's performance, Right? If the array is too large then this silly technique (algorithm) will be inefficient as it has to travel all way to the certain elements of the array till it find the matches. So, its performance depends on (decreases for large array) the number of elements (n) of the array.
We have put some statements to track the starting and ending time of the execution. Then, we are running the algorithm two times on two different arrays with different sizes. Each time you will run the program you will find more time consumption on the larger array than on the smaller array. Though time is not the factor to identify the performance here, but its showing you the decrement of performance in a way.

## O(n^2):

Now we will talk about an algorithm to sort elements of an array. According to its technique, it needs one iteration inside another iteration. In programming we call it using loop inside another loop. For those who does not know how bubble sort works - it makes multiple passes through an array. A "pass" is defined as one full trip through the array comparing and if necessary, swapping, adjacent elements. Several passes have to be made through the array before it is finally sorted. It compares adjacent items and exchanges those that are out of order. Each pass through the list places the next largest value in its proper place. Thats why it needs two loops to make this technique work. Check the below program,

```java
public class Main {
    private int[] theArray;
    private int arraySize;
    private int itemsInArray = 0;
    static long startTime;
    static long endTime;

    public static void main(String[] args) {
        Main testBubbleSortAlgo = new Main(10000);
        testBubbleSortAlgo.generateRandomArray();

        Main testBubbleSortAlgoAgain = new Main(90000);
        testBubbleSortAlgoAgain.generateRandomArray();

        testBubbleSortAlgo.bubbleSort();
        testBubbleSortAlgoAgain.bubbleSort();

    }

    Main(int size) {
        arraySize = size;
        theArray = new int[size];
    }

    public void bubbleSort() {

        startTime = System.currentTimeMillis();

        for (int i = arraySize - 1; i &gt; 1; i--) {

            for (int j = 0; j &lt; i; j++) { if (theArray[j] &gt; theArray[j + 1]) {

                    int temp = theArray[j];
                    theArray[j] = theArray[j+1];
                    theArray[j+1] = temp;

                }
            }
        }

        endTime = System.currentTimeMillis();

        System.out.println(&quot;Bubble Sort Took &quot; + (endTime - startTime));
    }

    public void generateRandomArray() {

        for (int i = 0; i &lt; arraySize; i++) {
            theArray[i] = (int) (Math.random() * 1000) + 10;
        }

        itemsInArray = arraySize - 1;

    }
}
```

[Try it Online](http://ideone.com/Ftqmee)

The important tasks that are happened inside the `bubbleSort` method are 1) Make all passes 2) Compare each adjacent (swap if needed) elements in each pass. So, this algorithm also performs differently based on the amount of data to be handled. Even, this algorithm become mad if the number of elements is too high. Because, both the "Number of Pass" and "Comparison &amp; Swapping" increases by a square rate. Hence, we can say that, the complexity of this algorithm is O(n^2).

## O(log_2 n)

Lastly we will checkout an algorithm which is also a searching algorithm like the Linear Search but it uses more intelligent trick to find out an element. What it does is - it takes a sorted Array and then divide all the elements into two parts and works only on one part. If the target value is larger than the middle of the split elements chain then it looks into the parts that contains higher half of elements. This algorithm divides its whole operational data elements into half every time it looks for the target elements. Thus, it makes the operational data amount half in each iteration.

```java
import java.util.Random;

public class Main {
    private int[] theArray;
    private int arraySize;
    private int itemsInArray = 0;
    static long startTime;
    static long endTime;

    public static void main(String[] args) {
        Main testBubbleSortAlgo = new Main(10000);
        testBubbleSortAlgo.generateSortedArray();

        Main testBubbleSortAlgoAgain = new Main(90000);
        testBubbleSortAlgoAgain.generateSortedArray();

        Random r = new Random();
        testBubbleSortAlgo.binarySearch(r.nextInt((10000 - 1) + 1) + 1);
        testBubbleSortAlgoAgain.binarySearch(r.nextInt((90000 - 1) + 1) + 1);

    }

    Main(int size) {
        arraySize = size;
        theArray = new int[size];
    }

    public void binarySearch(int value) {

        startTime = System.currentTimeMillis();

        int lowIndex = 0;
        int highIndex = arraySize - 1;

        int timesThrough = 0;

        while (lowIndex &lt;= highIndex) {

            int middleIndex = (highIndex + lowIndex) / 2;

            if (theArray[middleIndex] &lt; value) lowIndex = middleIndex + 1; else if (theArray[middleIndex] &gt; value)
                highIndex = middleIndex - 1;

            else {

                System.out.println(&quot;\nFound a Match for &quot; + value
                        + &quot; at Index &quot; + middleIndex);

                lowIndex = highIndex + 1;

            }

            timesThrough++;

        }

        endTime = System.currentTimeMillis();
        System.out.println(&quot;Binary Search Took &quot; + (endTime - startTime));
        System.out.println(&quot;Times Through: &quot; + timesThrough);
    }


    public void generateSortedArray() {

        for (int i = 0; i &lt; arraySize; i++) {
            theArray[i] = i;
        }

        itemsInArray = arraySize - 1;

    }
}
```

[Try it Online](http://ideone.com/YheZQv)

So, like every other algorithm lets inspect how it scales based on assigned amount of data. We, know that the total number of times you can divide a number by 2 is `O(log_2 n)` This algorithm also acts like this way. So, if the number of assigned data elements is n then complexity of the above algorithm/technique which is called Binary Search Algorithm is `O(log_2 n)`

This is how we identify and calculate complexity, efficiency and performance of any Algorithm for any specific task. So, before implementing any algorithm in any computational problem, we should first inspect the complexity of that algorithm. Otherwise, it may work fast and smoothly for less number of data but not for large amount of data set. So, logic and calculation trick known as algorithm needs to be finalized first before diving into writing code.

## Some Resources:

* https://visualgo.net/  
* https://interactivepython.org/runestone/static/pythonds/index.html  
* http://bigocheatsheet.com/  

> **Do you love Watching than Reading?**  
[Subscribe](https://www.youtube.com/channel/UCJFY9iVRXTJu1SPVI_vRNDw) & Get Connected with my [YouTube](https://www.youtube.com/channel/UCJFY9iVRXTJu1SPVI_vRNDw) channel for Video version of all my Blog posts.