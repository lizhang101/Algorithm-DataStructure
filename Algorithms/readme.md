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

## [Recursion](http://www.geeksforgeeks.org/recursion/)
The process in which a function calls itself directly or indirectly is called recursion and the corresponding function is called as recursive function.

In recursive program, the solution to base case is provided and solution of bigger problem is expressed in terms of smaller problems.

Examples of such problems are Towers of [Hanoi (TOH)](http://quiz.geeksforgeeks.org/c-program-for-tower-of-hanoi/), [Inorder/Preorder/Postorder Tree Traversals](http://www.geeksforgeeks.org/tree-traversals-inorder-preorder-and-postorder/), [DFS of Graph](http://www.geeksforgeeks.org/depth-first-traversal-for-a-graph/), etc.

### direct recursion vs indirect recursion
### tailed recursion vs non-tailed recursion
### recursive programming vs iterative programming

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

DP problems require you to spot the underlying subproblem so you can memoize or recurse through them. The key is to find the recurring subproblem.

### DP tutorials
- MIT 6.006 [DP I](https://www.youtube.com/watch?v=OQ5jsbhAv_M&list=PLUl4u3cNGP61Oq3tWYp6V_F-5jb5L2iHb&index=19&t=1970s)
- MIT 6.006 [DP II](https://www.youtube.com/watch?v=ENyox7kNKeY&list=PLUl4u3cNGP61Oq3tWYp6V_F-5jb5L2iHb&index=20)
- MIT 6.006 [DP III](https://www.youtube.com/watch?v=ocZMDMZwhCY&list=PLUl4u3cNGP61Oq3tWYp6V_F-5jb5L2iHb&index=21)
- MIT 6.006 [DP IV](https://www.youtube.com/watch?v=tp4_UXaVyx8&list=PLUl4u3cNGP61Oq3tWYp6V_F-5jb5L2iHb&index=22)
- MIT 6.046 [DP](https://www.youtube.com/watch?v=krZI60lKPek)

- CMU [dynamic programming](https://www.cs.cmu.edu/~avrim/451f09/lectures/lect1001.pdf)
- [Dynamic Programming – From Novice to Advanced](https://www.topcoder.com/community/data-science/data-science-tutorials/dynamic-programming-from-novice-to-advanced/)
- [Dynamic Programming | Set 1 (Overlapping Subproblems Property)](http://www.geeksforgeeks.org/dynamic-programming-set-1/)
- Read the _Dynamic programming chapter_ from _**Introduction to Algorithms**_ by Cormen...
- Geekforgeeks [Dynamic Programming](http://www.geeksforgeeks.org/dynamic-programming/)
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

- [Introduction To Backtracking Programming](http://algorithms.tutorialhorizon.com/introduction-to-backtracking-programming/)
- [Backtracking Algorithms](http://www.geeksforgeeks.org/backtracking-algorithms/)

### Backtracking [Questions](http://www.geeksforgeeks.org/category/algorithm/backtracking/)
- [Knight's Tour Problem](http://www.geeksforgeeks.org/backtracking-set-1-the-knights-tour-problem/)
- [Maze Problem](http://www.geeksforgeeks.org/backttracking-set-2-rat-in-a-maze/)
- [NQueens Problem](http://www.geeksforgeeks.org/backtracking-set-3-n-queen-problem/)
- [Subset Sum](http://www.geeksforgeeks.org/backttracking-set-4-subset-sum/)
- [mColoring Problem](http://www.geeksforgeeks.org/backttracking-set-5-m-coloring-problem/)
- [Hamiltonian Cycle](http://www.geeksforgeeks.org/backtracking-set-7-hamiltonian-cycle/)
- [SudoKu](http://www.geeksforgeeks.org/backtracking-set-7-suduku/)

# References
- Quora [How do I understand recursion in deep and all related field backtracking, dynamic programming and so on?](https://www.quora.com/How-do-I-understand-recursion-in-deep-and-all-related-field-backtracking-dynamic-programming-and-so-on)
- Geekforgeeks [algorithms](http://www.geeksforgeeks.org/fundamentals-of-algorithms/)
