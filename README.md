The Lettle Programming Language
===============================

Lettle is type-safe and purely functional programming language for JVM. It is in early development/design phase now. 
So, do not expect see all the sources avaliable and compilable.

The short list of features:
* Damas-Hindley-Milner Type Inference
* Algebraic Data Types: Tagged Unions, Records
* Pattern Matching
* Lazy Evaluation
* Memoization 
* Structural Typing ???

Here is the brief example:
```
// A tagged-union Tree
type Tree[A] = Branch of A * Tree * Tree ? Leaf

// A function with pattern-matching that fetchs the nth element of the tree
let nth[A](t: Tree[A], n: Int) = t
  ? Branch(_, l, _, s) when (n < s) -> nth(l, n) 
  ? Branch(_, _, r, s) when (n > s) -> nth(r, n - s - 1)
  ? Branch(v, _, _, _) -> v
  ! fail "There is no $n in this tree."
```
