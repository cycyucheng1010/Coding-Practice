# Best Time to Buy and Sell Stock
## Eazy
## 題意
* 給你一串數列prices和它的長度，會在最小值時購入某股票，並於買入後某時間時可賣出達到最大利益，求期間最大利益為何?

## 範例輸入輸出
* 測資一
```
Input: prices = [7,1,5,3,6,4]
Output: 5
Explanation: Buy on day 2 (price = 1) and sell on day 5 (price = 6), profit = 6-1 = 5.
Note that buying on day 2 and selling on day 1 is not allowed because you must buy before you sell.
```
* 測資二
```
Input: prices = [7,6,4,3,1]
Output: 0
Explanation: In this case, no transactions are done and the max profit = 0.
```
## 解題思路
* 首先設定變數min值為一個很大的數值方便更新，接著設最大期間利益一開始為0，透過for迴圈一個一個去找最小值，如果沒找到最小值則嘗試計算其間利益，若大於原本的值則更新。
* 時間複雜度: `O(n)`
* 程式碼
```c
int maxProfit(int* prices, int pricesSize) {
    int min=100000;
    int max_profit=0;
    for(int i=0;i<pricesSize;i++){
        if(prices[i]<min){
            min = prices[i];
        }
        else if(prices[i]-min>max_profit){
            max_profit=prices[i]-min;
        }
        else{
        //pass    
        }
    }
    return max_profit;
}
```