`A Binary Heap is a complete Binary Tree which is used to store data efficiently to get the max or min element based on its structure.`

A Binary Heap is either Min Heap or Max Heap. In a Min Binary Heap, the key at the root must be minimum among all keys present in Binary Heap. The same property must be recursively true for all nodes in Binary Tree. Max Binary Heap is similar to MinHeap. 

### Examples of Min Heap:
<img width="221" alt="image" src="https://github.com/soulnote/Revision-topics/assets/71943647/a12f2994-fc6c-47b8-92fa-4221b6de02c7">


How is Binary Heap represented? 
A Binary Heap is a Complete Binary Tree. A binary heap is typically represented as an array.

The root element will be at Arr[0].
The below table shows indices of other nodes for the ith node, i.e., Arr[i]:
- `Arr[(i-1)/2]`	Returns the parent node
- `Arr[(2*i)+1]`	Returns the left child node
- `Arr[(2*i)+2]`	Returns the right child node
  
The traversal method use to achieve Array representation is Level Order Traversal. Please refer to Array Representation Of Binary Heap for details.

![image](https://github.com/soulnote/Revision-topics/assets/71943647/d98820c5-21fc-4bd3-9c60-7763087e4f5e)


## Operations on Heap:
Below are some standard operations on min heap:

- `getMin():` It returns the root element of Min Heap. The time Complexity of this operation is O(1). In case of a maxheap it would be getMax().
- `extractMin():` Removes the minimum element from MinHeap. The time Complexity of this Operation is O(log N) as this operation needs to maintain the heap property (by calling heapify()) after removing the root.
- `decreaseKey():` Decreases the value of the key. The time complexity of this operation is O(log N). If the decreased key value of a node is greater than the parent of the node, then we don’t need to do anything. Otherwise, we need to traverse up to fix the violated heap property.
- `insert():` Inserting a new key takes O(log N) time. We add a new key at the end of the tree. If the new key is greater than its parent, then we don’t need to do anything. Otherwise, we need to traverse up to fix the violated heap property.
- `delete():` Deleting a key also takes O(log N) time. We replace the key to be deleted with the minimum infinite by calling decreaseKey(). After decreaseKey(), the minus infinite value must reach root, so we call extractMin() to remove the key.
Below is the implementation of basic heap operations. 


```java 
import java.util.*; 
  
// A class for Min Heap  
class MinHeap { 
      
    // To store array of elements in heap 
    private int[] heapArray; 
      
    // max size of the heap 
    private int capacity; 
      
    // Current number of elements in the heap 
    private int current_heap_size; 
  
    // Constructor  
    public MinHeap(int n) { 
        capacity = n; 
        heapArray = new int[capacity]; 
        current_heap_size = 0; 
    } 
      
    // Swapping using reference  
    private void swap(int[] arr, int a, int b) { 
        int temp = arr[a]; 
        arr[a] = arr[b]; 
        arr[b] = temp; 
    } 
      
      
    // Get the Parent index for the given index 
    private int parent(int key) { 
        return (key - 1) / 2; 
    } 
      
    // Get the Left Child index for the given index 
    private int left(int key) { 
        return 2 * key + 1; 
    } 
      
    // Get the Right Child index for the given index 
    private int right(int key) { 
        return 2 * key + 2; 
    } 
      
      
    // Inserts a new key 
    public boolean insertKey(int key) { 
        if (current_heap_size == capacity) { 
              
            // heap is full 
            return false; 
        } 
      
        // First insert the new key at the end  
        int i = current_heap_size; 
        heapArray[i] = key; 
        current_heap_size++; 
          
        // Fix the min heap property if it is violated  
        while (i != 0 && heapArray[i] < heapArray[parent(i)]) { 
            swap(heapArray, i, parent(i)); 
            i = parent(i); 
        } 
        return true; 
    } 
      
    // Decreases value of given key to new_val.  
    // It is assumed that new_val is smaller  
    // than heapArray[key].  
    public void decreaseKey(int key, int new_val) { 
        heapArray[key] = new_val; 
  
        while (key != 0 && heapArray[key] < heapArray[parent(key)]) { 
            swap(heapArray, key, parent(key)); 
            key = parent(key); 
        } 
    } 
      
    // Returns the minimum key (key at 
    // root) from min heap  
    public int getMin() { 
        return heapArray[0]; 
    } 
      
      
    // Method to remove minimum element  
    // (or root) from min heap  
    public int extractMin() { 
        if (current_heap_size <= 0) { 
            return Integer.MAX_VALUE; 
        } 
  
        if (current_heap_size == 1) { 
            current_heap_size--; 
            return heapArray[0]; 
        } 
          
        // Store the minimum value,  
        // and remove it from heap  
        int root = heapArray[0]; 
  
        heapArray[0] = heapArray[current_heap_size - 1]; 
        current_heap_size--; 
        MinHeapify(0); 
  
        return root; 
    } 
          
    // This function deletes key at the  
    // given index. It first reduced value  
    // to minus infinite, then calls extractMin() 
    public void deleteKey(int key) { 
        decreaseKey(key, Integer.MIN_VALUE); 
        extractMin(); 
    } 
      
    // A recursive method to heapify a subtree  
    // with the root at given index  
    // This method assumes that the subtrees 
    // are already heapified 
    private void MinHeapify(int key) { 
        int l = left(key); 
        int r = right(key); 
  
        int smallest = key; 
        if (l < current_heap_size && heapArray[l] < heapArray[smallest]) { 
            smallest = l; 
        } 
        if (r < current_heap_size && heapArray[r] < heapArray[smallest]) { 
            smallest = r; 
        } 
  
        if (smallest != key) { 
            swap(heapArray, key, smallest); 
            MinHeapify(smallest); 
        } 
    } 
      
    // Increases value of given key to new_val. 
    // It is assumed that new_val is greater  
    // than heapArray[key].  
    // Heapify from the given key 
    public void increaseKey(int key, int new_val) { 
        heapArray[key] = new_val; 
        MinHeapify(key); 
    } 
      
    // Changes value on a key 
    public void changeValueOnAKey(int key, int new_val) { 
        if (heapArray[key] == new_val) { 
            return; 
        } 
        if (heapArray[key] < new_val) { 
            increaseKey(key, new_val); 
        } else { 
            decreaseKey(key, new_val); 
        } 
    } 
} 
  
// Driver Code 
class MinHeapTest { 
    public static void main(String[] args) { 
        MinHeap h = new MinHeap(11); 
        h.insertKey(3); 
        h.insertKey(2); 
        h.deleteKey(1); 
        h.insertKey(15); 
        h.insertKey(5); 
        h.insertKey(4); 
        h.insertKey(45); 
        System.out.print(h.extractMin() + " "); 
        System.out.print(h.getMin() + " "); 
          
        h.decreaseKey(2, 1); 
        System.out.print(h.getMin()); 
    } 
} 
```
Output
2 4 1

### Applications of Heaps:
- `Heap Sort:` Heap Sort uses Binary Heap to sort an array in O(nLogn) time.
- `Priority Queue:` Priority queues can be efficiently implemented using Binary Heap because it supports insert(), delete() and extractmax(), decreaseKey() operations in O(log N) time. Binomial Heap and Fibonacci Heap are variations of Binary Heap. These variations perform union also efficiently.
- `Graph Algorithms:` The priority queues are especially used in Graph Algorithms like Dijkstra’s Shortest Path and Prim’s Minimum Spanning Tree.
  
Many problems can be efficiently solved using Heaps. See following for example.
a) K’th Largest Element in an array.
b) Sort an almost sorted array
c) Merge K Sorted Arrays.

