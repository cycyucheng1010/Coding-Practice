# Rotate Array
## Medium
## 題意
* 給一組數組num以及一個rotate次數k值，求最後結果(k不為負數)。
## 範例輸入輸出
* 測資一
```
Input: nums = [1,2,3,4,5,6,7], k = 3
Output: [5,6,7,1,2,3,4]
Explanation:
rotate 1 steps to the right: [7,1,2,3,4,5,6]
rotate 2 steps to the right: [6,7,1,2,3,4,5]
rotate 3 steps to the right: [5,6,7,1,2,3,4]
```
* 測資二
```
Input: nums = [-1,-100,3,99], k = 2
Output: [3,99,-1,-100]
Explanation: 
rotate 1 steps to the right: [99,-1,-100,3]
rotate 2 steps to the right: [3,99,-1,-100]

```
## 解題思路
* 首先我們去觀察input oput之間的關係，可以發現`[1,2,3,4,5,6,7]`和`[5,6,7,1,2,3,4]`除了題目說明的步驟外，可以去觀察怎麼交換比較容易，因此可以得到下面思考步驟：
    1. `[1,2,3,4,5,6,7]` -> `[7,6,5,4,3,2,1]`
    2. `[7,6,5,4,3,2,1]` -> `[5,6,7,4,3,2,1]`
    3. `[5,6,7,4,3,2,1]` -> `[5,6,7,4,3,2,1]`
* 這樣的過程剛好也是三步，也是就是其實可以把rotate想成是inverse的概念；當呼叫rotate後，rotate會執行k次inverse，範圍則洽好會是`(0,numsSize-1)`,`(0,k-1)`,`(k,numsSize-1)`這三種，為了預防k比numsSize大，故還會做一個k%numsSize的動作去歸納出numsSize種規律。
```c
void swap(int*a,int*b){
    int temp=0;
    temp= *a;
    *a = *b;
    *b = temp;
}
void reverse(int* nums,int start,int end){
    while(start<end){
        swap(&nums[start],&nums[end]);
        start++;
        end--;
    }
}
void rotate(int* nums, int numsSize, int k) {
    if(k!=0){
        k=k%numsSize;
        reverse(nums,0,numsSize-1);
        reverse(nums,0,k-1);
        reverse(nums,k,numsSize-1);
    }
    
}
```