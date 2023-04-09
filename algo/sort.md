## Quick Sort

- Looks like pre-order traversal a binary tree

```
def quick_sort(nums):
    left, right = 0, len(nums)
    index = partition(nums, left, right)
    self.quick_sort(nums[:index])
    self.quick_sort(nums[index:])

def partition(nums, left, right):
    pivot = nums[left]
    while left < right:
        while left < right and num[right] > pivot:
            right -= 1
        nums[left] = nums[right]
        while left < right and nums[left] <= pivot:
            left += 1
        nums[right] = nums[left]
    nums[left] = pivot
    return left
```

## Merge Sort

- Looks like post-order traversal a binary tree

```
def merge_sort(nums: List[int]) -> None:
    if len(nums) <= 1:
        return nums
    mid = len(nums) // 2
    left = merge_sort(nums[:mid])
    right merge_sort(nums[mid:])

    return merge(nums, left, right)

def merge(nums: List[int], left: List[int], right: List[int]) -> None:
    i, j = 0, 0
    res = []
    while i < len(left) and j < len(right):
        if left[i] < right[j]:
            res.append(left[i])
            i += 1
        else:
            res.append(left[i])
            j += 1
    res += left[i:]
    res += right[j:]
    return res

```
