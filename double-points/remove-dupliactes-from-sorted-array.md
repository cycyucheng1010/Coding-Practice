# Remove Duplicates from Sorted Array
## Eazy
## 題意
* 給你一個名為nums的矩陣，此矩陣已由小排到大，請你幫我把重複的矩陣元素去除，並回傳一個k值，k代表共有k個不同元素，系統會透過元素個數去做assertion來判斷元素值是否正確
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
Input: nums = [1,1,2]
Output: 2, nums = [1,2,_]
Explanation: Your function should return k = 2, with the first two elements of nums being 1 and 2 respectively.
It does not matter what you leave beyond the returned k (hence they are underscores).
```
* 測資二
```
Input: nums = [0,0,1,1,1,2,2,3,3,4]
Output: 5, nums = [0,1,2,3,4,_,_,_,_,_]
Explanation: Your function should return k = 5, with the first five elements of nums being 0, 1, 2, 3, and 4 respectively.
It does not matter what you leave beyond the returned k (hence they are underscores).
```
## 解題思路
* 看到remove element就要聯想到快慢指標這種方法，因此一開始假定slow=0，fast是for迴圈中的i從1開始，如果`nums[slow]!=nums[i]`則為不重複元素，將nums[k]值替代且k+=1，在程式最後的部分要k+1，因為會沒計算到最後一個element
* 程式碼
```c
int removeDuplicates(int* nums, int numsSize) {
    if(numsSize==0){
        return 0;
    }
    else{
        int k=0;
        for(int i=1;i<=numsSize-1;i++){
            if(nums[k]!=nums[i]){
                k++;
                nums[k]=nums[i]; 
            }
        }
        k+=1; //last element
        return k;
    }
       
}
```