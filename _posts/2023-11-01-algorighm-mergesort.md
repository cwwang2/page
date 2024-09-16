---
layout: post
title: Mergesort
subtitle: sorting algorithm
cover-img: /assets/img/path.jpg
thumbnail-img: /assets/img/thumb.png
share-img: /assets/img/path.jpg
tags: [algorithms, sorting]
author: Bruce Wang
---

## Mergesort
Merge sort is also a devide and conquer algorithm. Is will divide the array into two subarrays, sort each subarray and merge them into one. It's a stable sorting algorithm, which means that the same element in the array will be in the same order after sorting. It's also provides a worst-case time complexity of O(nlogn).

## Time complexity
- Worst case: O(nlogn)
- Average case: O(nlogn)
- Best case: O(nlogn)

## Space complexity
- Best case: O(n)
- Worst case: O(n)

```c++
void merge(vector<int>& nums, vector<int>& left, vector<int>& right){
    int i = 0;
    int j = 0;
    int k = 0;
    // merge two sorted arrays
    while(i < left.size() && j < right.size()){
        if(left[i] < right[j]){
            nums[k] = left[i];
            i++;
        }else{
            nums[k] = right[j];
            j++;
        }
        k++;
    }

    // copy the remaining elements
    while(i < left.size()){
        nums[k] = left[i];
        i++;
        k++;
    }
    // 
    while(j < right.size()){
        nums[k] = right[j];
        j++;
        k++;
    }
}
void mergesort(vector<int>& nums){
    if(nums.size() <= 1) return;

    // divide the array into two subarrays
    int mid = nums.size()/2;
    
    // copy the left and right subarrays
    vector<int> left(nums.begin(), nums.begin()+mid);
    vector<int> right(nums.begin()+mid, nums.end());
    
    // sort the left and right subarrays
    mergesort(left);
    mergesort(right);

    // merge the sorted subarrays
    merge(nums, left, right);
}
