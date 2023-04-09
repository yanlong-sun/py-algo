## Binary Heap

Like a compelete binary tree and save in an array. Use the index as the pointer. arr[0] is empty.

```
# index of the parent node
def parent(root: int) -> int:
    return root // 2

# index of the left child
def left(root: int) -> int:
    return root * 2

# index of the right child
def right(root: int) -> int:
    return root * 2 + 1
```

Binary heap can be further divided into `max heap` and `min heap`. The property of a max heap is that each node is greater than or equal to its two children, while a min heap's property is that each node is less than or equal to its children.

## Priority Queue

The priority queue data structure has a useful feature: when you insert or delete elements, the elements are automatically sorted, based on the underlying binary heap operations.

```
class MaxPQ:
    def __init__(self, cap:int):
        self.pq = [None] * (cap+1)
        self.size = 0

    def max(self) -> Key:
        """
        Returns the maximum element in the current queue
        """
        return self.pq[1]

    def insert(self, e: Key) -> None:
        """
        O(logK) Inserts the element e into the queue
        """
        self.size += 1
        self.pq[self.size] = 3
        self.swim(self.size)

    def delMax(self) -> Key:
        """
        O(logK) Deletes and returns the maximum element in the current queue
        """
        max = self.pq[1]
        self.swap(1, self.size)
        self.pq[self.size] = None
        self.size -= 1
        self.sink(1)
        return max

    def swim(self, x: int) -> None:
        """
        Moves the element at position x up the heap to maintain the maximum heap property
        """
        while (x>1) and self.less(self.parent(x), x):
            self.swap(self.parent(x), x)
            x = self.parent(x)

    def sink(self, x: int) -> None:
        """
        Moves the element at position x down the heap to maintain the maximum heap property
        """
        while self.left(x) <= self.size:
            max = self.left(x)
            if self.right(x) <= self.size and self.less(max, self.right(x)):
                max = self.right(x)
            if self.less(max, x):
                break
            self.swap(x, max)
            x = max

    def swap(self, i: int, j: int) -> None:
        """
        Swaps the two elements in the array
        """
        self.pq[i], self.pq[j] = self.pq[j], self.pq[i]

    def less(self, i: int, j: int) -> bool:
        """
        Returns True if pq[i] is less than pq[j]
        """
        return self.pq[i].compareTo(self.pq[j]) < 0

    def left(self, index: int) -> int:
        """
        Returns the index of the left child of the given element
        """
        return index * 2

    def right(self, index: int) -> int:
        """
        Returns the index of the right child of the given element
        """
        return index * 2 + 1

    def parent(self, index: int) -> int:
        """
        Returns the index of the parent of the given element
        """
        return index // 2

```
