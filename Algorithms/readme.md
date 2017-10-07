# Algorithm Basics
## Asymptotic analysis
Asymptotic analysis of an algorithm refers to defining the mathematical boundation/framing of its run-time performance. Using asymptotic analysis, we can very well conclude the best case, average case, and worst case scenario of an algorithm.

High level idea: suppress constant factors and lower-order terms.

- Asymptotic Notations
  - Ο Notation : the notation Ο(n) is the formal way to express the upper bound of an algorithm's running time.
  ```
  Ο(f(n)) = { g(n) : there exists c > 0 and n0 such that f(n) ≤ c.g(n) for all n > n0. }
  ```
  - Ω Notation : the notation Ω(n) is the formal way to express the lower bound of an algorithm's running time.
  ```
  Ω(f(n)) ≥ { g(n) : there exists c > 0 and n0 such that g(n) ≤ c.f(n) for all n > n0. }
  ```
  - θ Notation : the notation θ(n) is the formal way to express both the lower bound and the upper bound of an algorithm's running time.
  ```
  θ(f(n)) = { g(n) if and only if g(n) =  Ο(f(n)) and g(n) = Ω(f(n)) for all n > n0. }
  ```


## Greedy Algorithms
In greedy algorithm approach, decisions are made from the given solution domain. As being greedy, the closest solution that seems to provide an optimum solution is chosen.

Greedy algorithms try to find a localized optimum solution, which **may** eventually lead to globally optimized solutions. However, generally greedy algorithms do not provide globally optimized solutions.

## Divide and Conquer
In divide and conquer approach, the problem in hand, is divided into smaller sub-problems and then **each problem is solved independently**. When we keep on dividing the subproblems into even smaller sub-problems, we may eventually reach a stage where no more division is possible. Those "atomic" smallest possible sub-problem (fractions) are solved. The solution of all sub-problems is finally merged in order to obtain the solution of an original problem.

- Divide/Break
- Conquer/Solve
- Merge/Combine

Example: merge sort.

## Dynamic Programming
Dynamic programming approach is similar to divide and conquer in breaking down the problem into smaller and yet smaller possible sub-problems. But unlike, divide and conquer, these sub-problems are not solved independently. Rather, results of these smaller sub-problems are remembered and used for similar or overlapping sub-problems.

Dynamic programming is used where we have problems, which can be divided into similar sub-problems, so that their results can be **re-used**. Mostly, these algorithms are used for optimization.

- [Introduction To Dynamic Programming - Fibonacci Series](http://algorithms.tutorialhorizon.com/introduction-to-dynamic-programming-fibonacci-series/)

## Backtracking
### What is Backtracking Programming??

Recursion is the key in backtracking programming. As the name suggests we backtrack to find the solution. We start with one possible move out of many available moves and try to solve the problem if we are able to solve the problem with the selected move then we will print the solution else we will backtrack and select some other move and try to solve it. If none if the moves work out we will claim that there is no solution for the problem.

### Generalized Algorithm:
```
Pick a starting point.
while(Problem is not solved)
	For each path from the starting point.
		check if selected path is safe, if yes select it
                and make recursive call to rest of the problem
		If recursive calls returns true, then return true.
		else undo the current move and return false.
	End For
	If none of the move works out, return false, NO SOLUTON.
```

- [Backtracking Algorithms](http://www.geeksforgeeks.org/backtracking-algorithms/)
- [Backtracking Questions](http://www.geeksforgeeks.org/category/algorithm/backtracking/)
