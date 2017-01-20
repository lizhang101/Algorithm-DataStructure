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


## 
