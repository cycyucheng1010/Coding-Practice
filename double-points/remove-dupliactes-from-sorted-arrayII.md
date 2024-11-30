# Remove Duplicates from Sorted Array II
## Medium
## 題意
* 給你一個名為nums的矩陣，此矩陣已由小排到大，此矩陣可接受同一種元素出現兩次，並回傳一個k值，k代表共有k個不同元素，系統會透過元素個數去做assertion來判斷元素值是否正確
* 系統測試程式碼
```c
int[] nums = [...]; // Input array
int[] expectedNums = [...]; // The expected answer with correct length

int k = removeDuplicates(nums); // Calls your implementation

assert k == expectedNums.length;
for (int i = 0; i < k; i++) {
    assert nums[i] == expectedNums[i];
}
```
## 範例輸入與測資
* 測資一
```
Input: nums = [1,1,1,2,2,3]
Output: 5, nums = [1,1,2,2,3,_]
Explanation: Your function should return k = 5, with the first five elements of nums being 1, 1, 2, 2 and 3 respectively.
It does not matter what you leave beyond the returned k (hence they are underscores).
* 測資二
```
Input: nums = [0,0,1,1,1,1,2,3,3]
Output: 7, nums = [0,0,1,1,2,3,3,_,_]
Explanation: Your function should return k = 7, with the first seven elements of nums being 0, 0, 1, 1, 2, 3 and 3 respectively.
It does not matter what you leave beyond the returned k (hence they are underscores).
```
## 解題思路
* 看到remove element就要聯想到快慢指標這種方法，但這題單個元素可重複兩次，因此一開始假定slow=2，fast是for迴圈中的i從2開始，首先會從`nums[slow-2]`檢查起，如果`nums[slow-2]!=nums[i]`則為不重複3次某元素，將nums[k]值替代且k+=1，即可求得解。
* 要考慮若`numsSize<2`的這種情況，所以要透過一個if來直接return掉。
* 程式碼
```c
int removeDuplicates(int* nums, int numsSize) {
    if (numsSize <= 2){
        return numsSize;
    }
    
    int slow=2;
    for(int i=2;i<numsSize;i++){
        if(nums[i]!=nums[slow-2]){
            nums[slow]=nums[i];
            slow+=1;
        }
    } 
    return slow;
}
```