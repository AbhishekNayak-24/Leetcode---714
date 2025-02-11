# Leetcode---714
Best Time to Buy and Sell Stock  With Transaction Fee
//code in java
public class Solution {
    public int maxProfit(int[] prices, int fee) {
        int n = prices.length;
        int cash = 0;  // cash on hand if we do not have a stock
        int hold = -prices[0];  // cash on hand if we have one stock

        for (int i = 1; i < n; i++) {
            // Do we sell the stock or not?
            cash = Math.max(cash, hold + prices[i] - fee);
            // Do we buy the stock or not?
            hold = Math.max(hold, cash - prices[i]);
        }

        return cash;
    }

    public static void main(String[] args) {
        Solution solution = new Solution();
        int[] prices = {1, 3, 2, 8, 4, 9};
        int fee = 2;
        int result = solution.maxProfit(prices, fee);
        System.out.println("The maximum profit is: " + result); // Output: 8
    }
}
