
If you're only interested in the keys, you can iterate through the `keySet()` of the map:

```Map<String, Object> map = ...;```

```java
for (String key : map.keySet()) {
    // ...
}
```

If you only need the values, use `values()`:
```java
for (Object value : map.values()) {
    // ...
}
```
