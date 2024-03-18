# sorting arrays

* Sort the elements based on their end coordinates
```java
int[][] points = { { 1, 2 }, { 6, 8 }, {3,5} };
Arrays.sort(points, (a, b) -> Integer.compare(a[1], b[1]));//output:[[1,2],[3,5],[6,8]]
```

* Sort the 2d array elements based on their starting. If the starting coordin are equal, sort based on the ending coordinates.
```java
int[][] points = { { 1, 2 }, { 6, 8 }, {6,5} };
Arrays.sort(points, (a, b) -> {
            if (a[0] == b[0]) {
                return Integer.compare(a[1], b[1]);
            }
            return Integer.compare(a[0], b[0]);
        });
//output : [[1,2][6,5],[6,8]]
```
* Java Code to sort 2D Matrix according to any Column

```java
// Importing required classes
import java.util.*;
class sort2DMatrixbycolumn {

	// Function to sort by column
	public static void sortbyColumn(int arr[][], int col)
	{
		// Using built-in sort function Arrays.sort
		Arrays.sort(arr, new Comparator<int[]>() {
			@Override
			// Compare values according to columns
			public int compare(final int[] entry1,
							final int[] entry2)
			{

				// To sort in descending order revert
				// the '>' Operator
				if (entry1[col] > entry2[col])
					return 1;
				else
					return -1;
			}
		}); // End of function call sort().
	}

	// Main driver method
	public static void main(String args[])
	{
		int matrix[][] = { { 39, 27, 11, 42 },
						{ 10, 93, 91, 90 },
						{ 54, 78, 56, 89 },
						{ 24, 64, 20, 65 } };

		// Sorting the matrix by 3rd Column
		int col = 3;
		sortbyColumn(matrix, col - 1);

		// Printing the sorted matrix
		for (int i = 0; i < matrix.length; i++) {
			for (int j = 0; j < matrix[i].length; j++)
				System.out.print(matrix[i][j] + " ");
			System.out.println();
		}
	}
}
```
* Java code to sort 2D matrix row-wise
```java
import java.io.*;
import java.util.Arrays;

public class Sort2DMatrix {

	static int sortRowWise(int m[][])
	{
		// One by one sort individual rows.
		for (int i = 0; i < m.length; i++)
			Arrays.sort(m[i]);

		// printing the sorted matrix
		for (int i = 0; i < m.length; i++) {
			for (int j = 0; j < m[i].length; j++)
				System.out.print(m[i][j] + " ");
			System.out.println();
		}

		return 0;
	}

	// driver code
	public static void main(String args[])
	{
		int m[][] = { { 9, 8, 7, 1 },
					{ 7, 3, 0, 2 },
					{ 9, 5, 3, 2 },
					{ 6, 3, 1, 2 } };

		sortRowWise(m);
	}
}
```
* Java program to Sort a Subarray in Descending order Using Arrays.sort()
```java

// Importing Collections class and arrays classes
// from java.util package
import java.util.Arrays;
import java.util.Collections;

// Main class
public class GFG {

	// Main driver method
	public static void main(String[] args)
	{
		// Note that we have Integer here instead of
		// int[] as Collections.reverseOrder doesn't
		// work for primitive types.
		Integer[] arr = { 13, 7, 6, 45, 21, 9, 2, 100 };

		Arrays.sort(arr, Collections.reverseOrder());

		// Printing the array as generated above
		System.out.println("Modified arr[] : " + Arrays.toString(arr));
	}
}
```
* Java program to demonstrate Working of Comparator interface
```java


// Importing required classes
import java.io.*;
import java.lang.*;
import java.util.*;

// Class 1
// A class to represent a student.
class Student {
	int rollno;
	String name, address;

	// Constructor
	public Student(int rollno, String name, String address)
	{
		// This keyword refers to current object itself
		this.rollno = rollno;
		this.name = name;
		this.address = address;
	}

	// Used to print student details in main()
	public String toString()
	{
		return this.rollno + " " + this.name + " "
			+ this.address;
	}
}

// Class 2
// Helper class extending Comparator interface
class Sortbyroll implements Comparator<Student> {
	// Used for sorting in ascending order of
	// roll number
	public int compare(Student a, Student b)
	{
		return a.rollno - b.rollno;
	}
}

// Class 3
// Main class
class GFG {

	// Main driver method
	public static void main(String[] args)
	{
		Student[] arr
			= { new Student(111, "bbbb", "london"),
				new Student(131, "aaaa", "nyc"),
				new Student(121, "cccc", "jaipur") };

		System.out.println("Unsorted");

		for (int i = 0; i < arr.length; i++)
			System.out.println(arr[i]);

		// Sorting on basic as per class 1 created
		// (user-defined)
		Arrays.sort(arr, new Sortbyroll());

		System.out.println("\nSorted by rollno");

		for (int i = 0; i < arr.length; i++)
			System.out.println(arr[i]);
	}
}

```
