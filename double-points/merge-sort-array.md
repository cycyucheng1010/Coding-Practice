# Merge Sort Array
## Eazy
## 題意
* 提供兩個已經由小排到大的數組num1&num2，num1內有m個元素、num2內有n個元素，求將num1中0去掉且加入num2之值後的由小到大排序結果。
## 範例輸入輸出
* 測資一
```
Input: nums1 = [1,2,3,0,0,0], m = 3, nums2 = [2,5,6], n = 3
Output: [1,2,2,3,5,6]
Explanation: The arrays we are merging are [1,2,3] and [2,5,6].
The result of the merge is [1,2,2,3,5,6] with the underlined elements coming from nums1.
```
* 測資二
```
Input: nums1 = [1], m = 1, nums2 = [], n = 0
Output: [1]
Explanation: The arrays we are merging are [1] and [].
The result of the merge is [1].

```
* 測資三
```
Input: nums1 = [0], m = 0, nums2 = [1], n = 1
Output: [1]
Explanation: The arrays we are merging are [] and [1].
The result of the merge is [1].
Note that because m = 0, there are no elements in nums1. The 0 is only there to ensure the merge result can fit in nums1.

``` 
## 解題思路
* merge sort 是一種divide&conquer，時間複雜度為O(n log(n))，空間複雜度為O(n) or O(1)
    * 時間複雜度： 透過一次確認兩數值大小故為log(n),數組總長度為n故重組時需O(n) -> O(n log(n)) 
* 由於是已由小到大排好之兩數組，故可以透過最大值比較知道要如何重組數列
    * 透過雙指標方式比較，可以降低時間複雜度做到merge sort的效果。
* 程式碼
```c
void merge(int* nums1, int nums1Size, int m, int* nums2, int nums2Size, int n) {
    int p1 = m-1;
    int p2 = n-1;
    int p = m+n-1;
    while(p1>=0&&p2>=0){
        if(nums1[p1]>nums2[p2]){
            nums1[p]=nums1[p1];
            p1-=1;
        }
        else{
            nums1[p]=nums2[p2];
            p2-=1;
        }
        p--;
    }
    while(p2>=0){
        nums1[p]=nums2[p2];
        p2-=1;
        p-=1;
    }

}
```