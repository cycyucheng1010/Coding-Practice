# Remove Element
## Eazy
## 題意
* 給你一個矩陣nums以及一個val值，請你給我return一個**去掉val值後的矩陣nums元素個數k值**，系統會透過元素個數去做assertion來判斷元素值是否正確(扣出val後的排列不變)
* 系統測試程式碼
```c
int[] nums = [...]; // Input array
int val = ...; // Value to remove
int[] expectedNums = [...]; // The expected answer with correct length.
                            // It is sorted with no values equaling val.

int k = removeElement(nums, val); // Calls your implementation

assert k == expectedNums.length;
sort(nums, 0, k); // Sort the first k elements of nums
for (int i = 0; i < actualLength; i++) {
    assert nums[i] == expectedNums[i];
}
```
## 範例輸入輸出
* 測資一
```
Input: nums = [3,2,2,3], val = 3
Output: 2, nums = [2,2,_,_]
Explanation: Your function should return k = 2, with the first two elements of nums being 2.
It does not matter what you leave beyond the returned k (hence they are underscores).
```
* 測資二
```
Input: nums = [0,1,2,2,3,0,4,2], val = 2
Output: 5, nums = [0,1,4,0,3,_,_,_]
Explanation: Your function should return k = 5, with the first five elements of nums containing 0, 0, 1, 3, and 4.
Note that the five elements can be returned in any order.
It does not matter what you leave beyond the returned k (hence they are underscores).
```
## 解題思路
* 題目希望k是nums矩陣的前n個值，也就是說需要去改動矩陣的值，那可以透過快慢指標(slow&fast)的方式來處理，fast指標用來確認有沒有遇到val值，slow用來記錄有幾個值非val。
* 當遇到val時跳過不做，沒遇到則`nums[slow]=nums[fast]`，這樣的疊代方式可以讓後面非val的值往前達成會進行的虛擬judge
* 程式碼
```c
int removeElement(int* nums, int numsSize, int val) {
    int k =0;
    for(int i=0;i<=numsSize-1;i++){
        if(nums[i]!=val){
            nums[k]=nums[i];
            k+=1;
        }
    }
    return k;
}
```