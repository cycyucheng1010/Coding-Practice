# Majority Element
## Easy
## 題意
* 給一個數組nums以及他的長度n，請你求majority element。
* majority element：當某元素在數組中出現超過n/2次則成為majority element。
## 範例輸入輸出
* 測資一
```
Input: nums = [3,2,3]
Output: 3
```
* 測資二
```
Input: nums = [2,2,1,1,1,2,2]
Output: 2

```
## 解題思路
* 因為題目告訴我majority element的數量會大於n/2故可以想到排序完之後的中間值就是我們要的答案。
* 首先透過c內建的quick sort來快速排列，接著再透過找`nums[n/2]`的值解出答案。
```c
int compare(const void *a, const void *b){
    return (*(int*)a - *(int*)b);
}
int majorityElement(int* nums, int numsSize) {

    //qsort為C內建之quick sort function，透過減法判斷值的大小，參數分別為:(數組, 數組大小, 判斷函式的大小, 自己寫的函式)
    qsort(nums,numsSize,sizeof(int),compare); 
    return nums[numsSize/2];
}
```