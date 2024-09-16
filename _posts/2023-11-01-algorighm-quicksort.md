---
layout: post
title: Quicksort
subtitle: sorting algorithm
cover-img: /assets/img/path.jpg
thumbnail-img: /assets/img/thumb.png
share-img: /assets/img/path.jpg
tags: [algorithms, sorting]
author: Bruce Wang
---

## Quicksort
Quick sort is a divide and conquer algorithm. It picks an element as pivot and partitions the given array around the picked pivot. There are many different versions of quickSort that pick pivot in different ways.
Every time we partition the array, we get two subarrays. The pivot is in its final sorted position. The elements in left subarray are smaller than the pivot, and the elements in right subarray are greater than the pivot. Then, we apply the same steps recursively to the subarrays.

### Time Complexity
- Worst case: O(n^2)
- Average case: O(nlogn)
- Best case: O(nlogn)

### Space complexity
- Best case: O(logn)
- Worst case: O(n)

```c++
int partition(vector<int> nums, int left, int right){
    int pivot = nums[right];
    int i = left - 1;
    for(int j = left; j < right; j++){
        if(nums[j] < pivot){
            i++;
            swap(nums[i], nums[j]);
        }
    }
    swap(nums[i+1], nums[right]);
    return i+1;
}

void quicksort(vector<int> nums, int left, int right){
    if(left < right){
        int pivot = partition(nums, left, right);
        quicksort(nums, left, pivot-1);
        quicksort(nums, pivot+1, right);
    }
}
```