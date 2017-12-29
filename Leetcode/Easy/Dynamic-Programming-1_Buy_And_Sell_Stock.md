# [121. Best Time to Buy and Sell Stock](https://leetcode.com/problems/best-time-to-buy-and-sell-stock)
## Problem Description
Say you have an array for which the ith element is the price of a given stock on day i.

If you were only permitted to complete at most one transaction (ie, buy one and sell one share of the stock), design an algorithm to find the maximum profit.
```
Example 1:
Input: [7, 1, 5, 3, 6, 4]
Output: 5

max. difference = 6-1 = 5 (not 7-1 = 6, as selling price needs to be larger than buying price)
Example 2:
Input: [7, 6, 4, 3, 1]
Output: 0
```
In this case, no transaction is done, i.e. max profit = 0.

## Solution
Basic idea is try to buy the stock at the lowest price, and sell it at the highest price after the day you buy it.
```
var maxProfit = function(prices) {
    if (!prices.length)   return 0;
    let min = prices[0];
    let profit = 0;
    for (let price of prices) {
        min = Math.min(min, price);
        profit = Math.max(profit, price - min);
    }
    return profit;
};
```

# [122. Best Time to Buy and Sell Stock II](https://leetcode.com/problems/best-time-to-buy-and-sell-stock-ii)
## Problem Description

## Solution


# [309. Best Time to Buy and Sell Stock with Cooldown](https://leetcode.com/problems/best-time-to-buy-and-sell-stock-with-cooldown)
## Problem Description

## Solution


# [714. Best Time to Buy and Sell Stock with Transaction Fee](https://leetcode.com/problems/best-time-to-buy-and-sell-stock-with-transaction-fee)
## Problem Description

## Solution


# [123. Best Time to Buy and Sell Stock III](https://leetcode.com/problems/best-time-to-buy-and-sell-stock-iii)
## Problem Description

## Solution


# [188. Best Time to Buy and Sell Stock IV](https://leetcode.com/problems/best-time-to-buy-and-sell-stock-iv)
## Problem Description

## Solution

