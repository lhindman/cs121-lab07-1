# Module 7 Lab Guide (part 1)
## Getting Started
[Lab Introduction Video](https://youtu.be/y6G2ucQTEBw)

### Code Style Requirements
Please review the [CS121 Style Guide](https://docs.google.com/document/d/1LWbGQBKkApnNAzzgwOSvRM03DmhYWx5yEfecT2WXfjI/edit?usp=sharing) and apply it in all lab activities and projects this semester. Coding Style will assessed as part of your lab and project grades.

### Code Quality Requirements
- Code must compile without warnings using openjdk 11
- Code must run without errors or warnings on safe-path and edge test cases
- More to come as we learn about input validation and exception handling  

## Lab Warmup - NumberStats
### Problem Description
Design and implement an application that creates an array that is a user specified size containing random numbers in the range of 1 to 100 (inclusive). The user will also specify a seed value so that the results we generate are reproducable. This array of random numbers will be used to generate a histogram that allows the user to visually inspect the frequency distribution of the set of random values. The program should produce a chart similar to the following <that indicates how many input values fell in the range 1 to 10, 11 to 20, and so on. Print one asterisk for each value entered.

     1 - 10   | *****  
    11 - 20   | **  
    21 - 30   | *************************  
    31 - 40   |   
    41 - 50   | ***  
    51 - 60   | *******  
    61 - 70   | **  
    71 - 80   | *****  
    81 - 90   | *******  
    91 - 100  | *********  

### Program Design
There are countless ways to solve this problem, however the objective of this activity is to gain experience working with Arrays and Methods.  To that end, we will design our solution to use three static methods.  The first method is called **generateRandomData()** and it takes a numElements and a seed value as parameters.  This method instantiates an array with the specified number of elements, loads it with random data using the seed value, and returns a reference to the caller. The second method is called **displayArray()** and it takes an array as a parameter and simply prints each element to the console.  The final method is called **generateHistogram()** and it takes an array as a parameter and returns a String containing a chart as shown above.

#### Static Methods
Use the following javadoc comments to implement the required functionality in the ArrayUtilities class.
```
/**
* Instantiate an integer array with the specified number
*    of elements and initialized it with random numbers 
*    in the range of 1 - 100 (inclusive).  Use the specified
*    seed value to initialize the Random object.
* 
* Return the array to the caller.
* @param numElements Size of the array
* @param seeed Value used to seed the Random object
* @return int array initialized with random values
*/
public static int[] generateRandomData(int numElements, long seed) {...}
```

```
/**
* Display the contents of the specified integer array in the console
*    on a single line, with commas separating the values as shown in 
*    the following example:
* 
*    83, 51, 77, 90, 96, 58, 35
* 
*    Notice that there is not a comma following the last value
* 
* @param data Array of integer data to be displayed
*/
public static void displayArray(int[] data) {...}
```

```
/**
* Generate a String containing a histogram showing the distribution over the
*    range of 1 - 100 (inclusive), divided into bins 10 bins of 10.  The 
*    output should be formatted as shown in the lab guide.
* @param data Array of interger values to be processed
* @return String containing the formatted histograom for the provided data.
*/
public static String generateHistogram(int[] data) {...}
```

#### Driver class
Add code to the main() method in NumberStats.java that uses a Scanner to prompt the user for the desired number of elements to generate and a seed value. Pass these values as arguments to the ArrayUtilities.generateRandomData() static method and stored the returned array to a local reference variable of the appropriate type. Use the ArrayUtilities.displayArray() static method to confirm that the array of random numbers is being generated properly, but do not leave this enabled in the fimal version of the program.  

Once it has been confirmed that the array of random ints is being generated properly, pass the array as an argument to the ArrayUtilities.generateHistogram() static method and store the return String containing the chart data to a local reference variable.  Finally, display the chart String data in the console using the System.out.println() method.

#### Expected Program Output (with sample user input)
```
-----------------------------
|   Simulation Parameters   |
-----------------------------
Please enter the desired number of random values: 25 
Please enter the seed value: 123

-----------------------------
|     Generated Values      |
-----------------------------
83, 51, 77, 90, 96, 58, 35, 38, 86, 54, 40, 27, 73, 66, 38, 50, 21, 86, 55, 17, 23, 38, 37, 51, 79

-----------------------------
|         Histogram         |
-----------------------------
  1 - 10  | 
 11 - 20  | *
 21 - 30  | ***
 31 - 40  | ******
 41 - 50  | *
 51 - 60  | *****
 61 - 70  | *
 71 - 80  | ***
 81 - 90  | ****
 91 - 100 | *
```

### Implementation Guide
1. Expand the folder named NumberStats and open both ArrayUtilities.java and NumberStats.java
2. Design a program to satisfy the requirements in the Problem Description and Program Design sections
3. Test the program using the sample user input and compare against the expected output.
4. Commit the changes to your local repository with a message stating that Lab Warmup is completed.
5. Push the changes from your local repository to the github classroom repository.
6. Take a break, you've earned it. :)

## Lab Activity 1 - BubbleSorter
### Problem Description
Design and implement an application that fills an array with random numbers, then uses the Bubble Sort algorithm described below to sort the contents of the array in ascending order. As sorting algorithms go, Bubble sort is one of the worst in terms of performance, but it does have the benefit of being one of the easiest to conceptualize and implement. :) Wikipedia provides an excellent discussion of the [Bubble Sort algorithm](https://en.wikipedia.org/wiki/Bubble_sort) as well as visualizations of the sorting process that may be helpful.

Pseudocode is a way of demonstrating how code should be written without getting bogged down in the details of a particular language. When I am sketching out a program on a whiteboard, I often use pseudocode to represent the structure of my program because my whiteboard doesn't care about datatypes or semicolons. :)

Below is a pseudocode implementation of the Bubble Sort algorithm. The indentations are important because they represent code blocks.
```
function sort(dataArray):
    	while !done
	done = True
	for( i = 1; i < dataArray.length; i++)
		if (dataArray[i-1] > dataArray[i])
			swap(i-1,i,dataArray)
			done = False
```

### Program Design
Begin by copying ArrayUtilities.java from the NumberStats folder into the BubbleSorter folder.  This will allow us to reuse both the generateRandomData() and displayArray() static methods. The first method we will implement is a private static method called swap(). It takes two indexes (positions) as well as an array reference as parameters and it will swap the values at the respective positions within the array. This method is made private as we only want it to be accessible from methods inside the ArrayUtilities class.  The second method is a public static method called sort(). It takes an array as a parameter and uses the Bubble sort algorithm shown above to sort the values. 

#### Static Methods
Use the following javadoc comments to implement the required functionality in the ArrayUtilities class.

```
/**
* Swap the values at the positions indicated by index1 and index2
*    within the data array. This method modifies the array referenced
*    by the variable data. Nothing is returned by the method.
* 
* @param index1 Position of value within data array to swap
* @param index2 Position of value within data array to swap
* @param data Reference to an array of integers containing values to be swapped
*/
private static void swap(int index1, int index2, int[] data) {...}
```

```
/**
* Sort the integer values in the array refeferenced by data in ascending order
*     using the Bubble Sort algorithm. This method modifies the array referenced
*    by the variable data. Nothing is returned by the method.
* 
* @param data Reference to an array of integers to be sorted
*/
public static void sort(int[] data) {...}
```

#### Driver class
Add code to the main() method in BubbleSorter.java that uses a Scanner to prompt the user for the desired number of elements to generate and a seed value. Pass these values as arguments to the ArrayUtilities.generateRandomData() static method and stored the returned array to a local reference variable of the appropriate type. Use the ArrayUtilities.displayArray() static method to display the unsorted values and include a header stating that this is the unsorted data.

Once it has been confirmed that the array of random ints is being generated properly, pass the array as an argument to the ArrayUtilities.sort() static method, then call ArrayUtilities.displayArray() again, this time with a message stating that this is the sorted data.

#### Expected Program Output (with sample user input)
```
-----------------------------
|   Simulation Parameters   |
-----------------------------
Please enter the desired number of random values: 25
Please enter the seed value: 123

-----------------------------
|     Generated Values      |
-----------------------------
83, 51, 77, 90, 96, 58, 35, 38, 86, 54, 40, 27, 73, 66, 38, 50, 21, 86, 55, 17, 23, 38, 37, 51, 79

-----------------------------
|        Sorted Values      |
-----------------------------
17, 21, 23, 27, 35, 37, 38, 38, 38, 40, 50, 51, 51, 54, 55, 58, 66, 73, 77, 79, 83, 86, 86, 90, 96
```
### Impementation Guide
1. Expand the folder named BubbleSorter, copy ArrayUtilities.java from NumberStats folder and open both ArrayUtilities.java and BubbleSorter.java
2. Design a program to satisfy the requirements in the Problem Description and Program Design sections
3. Test the program using the sample user input and compare against the expected output.
4. Commit the changes to your local repository with a message stating that Lab Activity 1 is completed.
5. Push the changes from your local repository to the github classroom repository.

## Coding Journal (Optional)
Keep a journal of your activities as you work on this lab. Many of the best engineers that I have worked with professionally have kept some sort of engineering journal. I personally packed notebooks around with me for nearly 8 years before I began keeping my notes electronically.   

Your journal can track ideas, bugs, cool links, code snippets, shell commands, rants, or simply a reflection on what worked well or not-so-well with this lab activity. I will not be grading the content of your journal, but I will expect at least two timestamped journal entries of at least a 75 to 150 words each added to the provided Journal.md file.  The purpose of this component is to help develop the habit of taking notes and creating documentation while you code. The more detail you provide the better as that will help you if you ever need to refer back to this project in the future.

## Markdown Resources
Markdown is a notation that is used to format text documents.  It is widely used in Software Development shops around the world, which is why we're asking you to use it in your lab documentation.  

Github provides a guide for getting started:  [Mastering Markdown](https://guides.github.com/features/mastering-markdown/)
