You can use `StringBuilder` to sort characters, but it won't directly give you a sorted string. `StringBuilder` provides methods for appending, inserting, deleting, and modifying characters in a sequence, but it doesn't inherently sort characters.

To sort characters, you need to convert the `StringBuilder` to a string and then sort that string. However, since strings in Java are immutable, sorting a string directly isn't possible. Instead, you would typically convert the `StringBuilder` to a character array and then sort the array using `Arrays.sort()` method.

Here's an example of how you can sort characters using `StringBuilder`:

```java
StringBuilder sb = new StringBuilder("cba");
char[] charArray = sb.toString().toCharArray();
Arrays.sort(charArray);
String sortedStr = new String(charArray); // Now you have "abc"
```

So, while you can use `StringBuilder` to manipulate characters, it requires additional steps to sort them compared to using `String`. In the context of your problem, sorting individual strings directly with `StringBuilder` would require these additional steps, making the code more complex. Therefore, it's simpler and more efficient to use `String` directly, convert it to a character array, sort the array, and then create a new string.
