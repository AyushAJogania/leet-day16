# leet-day16

# Strange Printer

## Problem Description

You are given a string `s`. There is a strange printer with the following two special properties:

1. The printer can only print a sequence of the same character each time.
2. At each turn, the printer can print new characters starting from and ending at any place and will cover the original existing characters.

You need to find the minimum number of turns the printer needed to print the given string `s`.

## Solution Approach

We can use dynamic programming to solve this problem efficiently. We define a recursive function `f(i, j, s)` that calculates the minimum number of turns needed to print the substring `s[i:j+1]`.

1. We create a memoization table `dp` of size `n x n` (where `n` is the length of string `s`) to store the results of the recursive function calls.

2. In the `f` function, we check if the result for the substring `s[i:j+1]` is already calculated and stored in the `dp` table. If yes, we return the stored result.

3. We handle the base case when `i == j`, which means we have a single character in the substring. In this case, the minimum number of turns required is 1, so we return 1.

4. Next, we check if the first and last characters of the substring are the same or if the last character is the same as the one before it. In these cases, we can print the substring with one turn, so we call the recursive function with a reduced substring `s[i:j]` and store the result in the `dp` table.

5. If the first and last characters are not the same and the last character is also not the same as the one before it, we need to split the substring into two parts. We try all possible splitting positions `k` (where `i < k < j`) and find the minimum number of turns required for each split. We then take the minimum of these values and store it in the `dp` table.

6. Finally, we return the calculated result for the original substring `s[i:j+1]`.

7. In the `strangePrinter` function, we initialize the memoization table `dp` and call the recursive function `f` with the full string `s` (i.e., `f(0, n-1, s)`). The result of the function call will be the minimum number of turns needed to print the entire string.

## Complexity Analysis

The time complexity of the solution is O(n^3), where `n` is the length of the input string `s`. This is because we have a nested loop over all possible splitting positions in the recursive function.

The space complexity of the solution is O(n^2) for the memoization table `dp`.
