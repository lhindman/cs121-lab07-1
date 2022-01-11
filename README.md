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
Design and implement an application that creates an array that is a user specified size containing random numbers in the range of 1 to 100 (inclusive). The user will also specify a seed value so that the results we generate are reproducable. This array of random numbers will be used to generate a histogram that allows the user to visually inspect the frequency distribution of the set of random values. The program should produce a chart similar to the following on that indicates how many input values fell in the range 1 to 10, 11 to 20, and so on. Print one asterisk for each value entered.

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
public static int[] generateRandomData(int numElements, long seed) {...}
```

```
public static void displayArray(int[] data) {...}
```

```
public static String generateHistogram(int[] data) {...}
```

#### Driver class
Add code to the main() method in NumberStats.java that uses a Scanner to prompt the user for the desired number of elements to generate and a seed value. Pass these values as arguments to the ArrayUtilities.generateRandomData() static method and stored the returned array to a local reference variable of the appropriate type. Use the ArrayUtilities.displayArray() static method to confirm that the array of random numbers is being generated properly, but do not leave this enabled in the fimal version of the program.  

Once it has been confirmed that the array of random ints is being generated properly, pass the array as an argument to the ArrayUtilities.generateHistogram() static method and store the return String containing the chart data to a local reference variable.  Finally, display the chart String data in the console using the System.out.println() method.

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
			swap(i-1,i)
			done = False
```

### Program Design
Begin by copying ArrayUtilities.java from the NumberStats folder into the BubbleSorter folder.  This will allow us to reuse both the generateRandomData() and displayArray() static methods. 

### Impementation Guide
1. Expand the folder named A3-BubbleSorter and create two new files named BubbleSorter.java and Driver.java
2. Implement the program as specified in the BubbleSorter Activity Guide
3. Test the program using the run link above the main method
4. Commit the changes to your local repository with a message stating that Activity 3 is completed.
5. Push the changes from your local repository to the github classroom repository.


## Activity 4 - QuickDraw Game
### Problem Description
Design and implement an application that plays the Quick Draw Game.  

The details for this activity are in the guide below:

[QuickDraw Activity Guide](https://docs.google.com/document/d/1wickOaQSKScPR0EAizBDAdmYBEj1JXJwiNuzzFji8-Q/edit?usp=sharing)

### Impementation Guide
1. Expand the folder named A4-QuickDraw and create two new files named DeckOfCards.java and QuickDraw.java
2. Implement the program as specified in the QuickDraw Activity Guide
3. Test the program using the run link above the main method
4. Commit the changes to your local repository with a message stating that Activity 4 is completed.
5. Push the changes from your local repository to the github classroom repository.

## Activity 5 - Gradebook Revisited
### Problem Description
Redesign the Gradebook application created in Lab05 to use arrays instead of the ArrayList class.  The initial size of the gradebook internal array should start at 4 elements and should used the heuristic discussed in the lecture to grow the array by doubling its size each time it runs out of space.  A gradebook csv file containing 1000+ student records has been provided.

### Implementation Guide
1. Copy Gradebook.java, Student.java, and gradebook.csv from Lab05 into the A5-Gradebook folder.
2. Modify Gradebook.java satisfy the requirements in the Problem Description 
3. Test the program using the gradebook-xl.csv dataset
4. Commit the changes to your local repository with a message stating that Activity 5 is completed.
5. Push the changes from your local repository to the github classroom repository


