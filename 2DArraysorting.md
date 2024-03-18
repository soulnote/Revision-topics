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
