---
title: Remove Duplicated from Sorted Array
date: 11-01-2022
categories:
- Algorithm
tags:
- Algorithm
---


#### Description

    Given an integer array nums sorted in non-decreasing order, remove the duplicates in-place such that each unique element appears only once. The relative order of the elements should be kept the same.
    Since it is impossible to change the length of the array in some languages, you must instead have the result be placed in the first part of the array nums. More formally, if there are k elements after removing the duplicates, then the first k elements of nums should hold the final result. It does not matter what you leave beyond the first k elements.
    Return k after placing the final result in the first k slots of nums.
    Do not allocate extra space for another array. You must do this by modifying the input array in-place with O(1) extra memory.
    
    
Example 1:

    Input: nums = [1,1,2]
    Output: 2, nums = [1,2,_]
    Explanation: Your function should return k = 2, with the first two elements of nums being 1 and 2 respectively.
    It does not matter what you leave beyond the returned k (hence they are underscores).

Example 2:

    Input: nums = [0,0,1,1,1,2,2,3,3,4]
    Output: 5, nums = [0,1,2,3,4,_,_,_,_,_]
    Explanation: Your function should return k = 5, with the first five elements of nums being 0, 1, 2, 3, and 4 respectively.
    It does not matter what you leave beyond the returned k (hence they are underscores).


#### Thinking
1. Declare two variables, pointer1 and pointer2
2. pointer1 records the first position of the number in the array 
3. pointer2 records the position of the latest duplicated number appeared in the array
4. traverse array, check if pointer1 is equal to pointer2, 
5. if true, move pointer2 to the next index position
6. if false, which means the number in the pointer2 position is unique, we need to move the unique number to the front 
7. so, we move pointer1 to the next index position, and give the latest value in the pointer2 position to the new pointer1 position
8. until the loop end, we can return the pointer1+1, since we need to total count of the unique numbers in the array, pointer1 is just the index

```javascript
    /**
     * @param {number[]} nums
     * @return {number}
     */
    
    let removeDuplicates = (nums)=>{
      if(nums.length === 0) return
    let pointer1 = 0
    for(let pointer2 = 1; pointer2 < nums.length; pointer2){
      if(nums[pointer1] !== nums[pointer2]){
        // when the numbers are not equal,  we need to give the value of nums[pointer2] to the new nums[pointer1]
        pointer1++
        nums[pointer1] = nums[pointer2]
      }
    }
    // pointer1 is index, but the problem needs us return the count of the unique numbers in the array
    return pointer1 + 1
  }

```