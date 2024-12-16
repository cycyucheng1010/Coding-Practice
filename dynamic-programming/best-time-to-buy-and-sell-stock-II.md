# Best Time to Buy and Sell Stock II
## Eazy
## 題意
* 給你一串數列prices和它的長度，讓你計算做完所有波段後總共可以賺多少錢

## 範例輸入輸出
* 測資一
```
Input: prices = [7,1,5,3,6,4]
Output: 7
Explanation: Buy on day 2 (price = 1) and sell on day 3 (price = 5), profit = 5-1 = 4.
Then buy on day 4 (price = 3) and sell on day 5 (price = 6), profit = 6-3 = 3.
Total profit is 4 + 3 = 7.
```
* 測資二
```
Input: prices = [1,2,3,4,5]
Output: 4
Explanation: Buy on day 1 (price = 1) and sell on day 5 (price = 5), profit = 5-1 = 4.
Total profit is 4.
```
## 解題思路
* 與easy的`best time to buy and sell stock`不一樣的點在於只要手上沒有股票就可以購買，透過測資二我們可以思考出一個道理：
`5-1 = (2-1)+(3-2)+(4-3)+(5-4)`，也就是說其他你趕快賣掉跟你拖很久才賣掉並不影響甚至可能更好(因為沒有手續費問題)，依照這個邏輯我就比`prices[i]`和`prices[i-1]`的值即可。
* 時間複雜度: `O(n)`
* 程式碼
```c
int maxProfit(int* prices, int pricesSize) {
    int max_profit=0;
    for(int i=1;i<pricesSize;i++){
        if(prices[i]-prices[i-1]>0){
            max_profit+=(prices[i]-prices[i-1]);
        }
    }
    return max_profit;
}
```