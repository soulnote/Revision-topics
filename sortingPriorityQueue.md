
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
