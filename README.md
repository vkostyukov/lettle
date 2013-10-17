The Lettle Programming Language
===============================

Lettle is type-safe and purely functional programming language for JVM. It is in early development/design phase now. 
So, do not expect see all the sources avaliable and compilable.

The short list of features:
* Damas-Hindley-Milner Type Inference
* Compound Data Types: Tagged Unions, Records
* Pattern Matching
* Lazy Evaluation
* Memoization 
* Structural Typing ???

Here is the brief example:
```
// A tagged-union Tree
union Tree[A] = Branch of A * Tree * Tree ? Leaf

// A function with pattern-matching that fetchs the nth element of the tree
let nth[A](t: Tree[A], n: Int) = t
  ? Branch(_, l, _, s) when (n < s) -> nth(l, n) 
  ? Branch(_, _, r, s) when (n > s) -> nth(r, n - s - 1)
  ? Branch(v, _, _, _) -> v
  ! fail "There is no $n in this tree."
```

How to use standard library `lang.let` (Project Euler #1):
```
let euler1 = Range(1, 999) | filter {x} -> (x % 3 == 0 || x % 5 == 0) | fold _ + _
```

```
tuple Student(name: String, rank: Int)

let students = List(Tuple("Ivan", 16), Tuple("Pavel", 22), Tuple("Denis", 24), Tuple("Igor", 22))

let goodStudents = students | filter {Student(_, r)} -> r >= 22

let printGoodStudents = goodStudents| foreach {Student(n, r)} -> println "A good student: $n (rank is $r)"
```

You can read [The Lettle Language Specification](https://github.com/vkostyukov/lettle/wiki/Specification).
