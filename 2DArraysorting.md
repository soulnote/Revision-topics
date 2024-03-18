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
