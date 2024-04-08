
## Ways to Sort a Priority Queue in Reverse Order in Java

### Using `Collections.reverseOrder()`
The `Collections.reverseOrder()` method returns a comparator that imposes the reverse of the natural ordering on a collection of objects that implement the Comparable interface. To use this method, you can pass it to the constructor of the PriorityQueue class. For example:
```java
PriorityQueue<Integer> pq = new PriorityQueue<>(Collections.reverseOrder());
```
This will create a priority queue that sorts its elements in reverse order.

### Custom Comparator
You can also use a custom comparator to sort a priority queue in reverse order. To do this, you need to implement the Comparator interface and provide a compare() method that compares two elements of the queue and returns an integer value indicating whether the first element is less than, equal to, or greater than the second element. For example:
```java
class ReverseComparator implements Comparator<Integer> {
    @Override
    public int compare(Integer o1, Integer o2) {
        return o2 - o1;
    }
}

PriorityQueue<Integer> pq = new PriorityQueue<>(new ReverseComparator());
```
This will create a priority queue that sorts its elements in reverse order using the custom comparator.

### Using Lambda Expression
Java 8 introduced a new syntax for lambda expressions. You can use a lambda expression to create a comparator that sorts elements in reverse order. For example:
```java
PriorityQueue<Integer> pq = new PriorityQueue<>((a, b) -> b - a);
```
This will create a priority queue that sorts its elements in reverse order using the lambda expression.

# Custom sorting in PQ
Given a class in a source code
```java
class Pair{
        int diff,val;
        public Pair(int diff,int val){
            this.diff=diff;
            this.val=val;
        }
    }
```
We have to modify the PriorityQueue sorting structure using comparator i such a way that it is sorted in order of `diff` member of the class and if its equal then we copare on the basis of `val` member.
```java
PriorityQueue<Pair> pq=new PriorityQueue<>(new Comparator<Pair>(){
            public int compare(Pair p1,Pair p2){
                if(p2.diff == p1.diff) return p2.val-p1.val;
                return p2.diff-p1.diff;
            }
        });
```
