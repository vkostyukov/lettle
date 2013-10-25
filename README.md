The Lettle Programming Language
===============================

Lettle is type-safe and purely functional programming language for JVM. [The Lettle Language Specification](https://github.com/vkostyukov/lettle/wiki/Specification).

* Damas-Hindley-Milner Type Inference
* Compound Data Types: Tagged Unions, Records
* Pattern Matching
* Structural Typing ???

### Examples

[_Project Euler #1_](http://projecteuler.net/problem=1)
```
let euler1 = Range(1, 999) | filter {x -> (x % 3 == 0 || x % 5 == 0)} | reduce _ + _
```

[_Project Euler #5_](http://projecteuler.net/problem=5)
```
let check(n: Int) = Range(1, 20) | fold(true) {acc, x -> acc && n % x == 0}
let loop(n: Int) = if (check(n)) n else loop(n + 1)
let euler5 = loop(20)
```

[_Project Euler #6_](http://projecteuler.net/problem=6)
```
let sumOfSquares = Range(1, 1000) | map {x -> x * x} | reduce _ + _
let squareOfSum = Range(1, 1000) | reduce _ + _ | x -> x * x
let euler6 = sumOfSquares - squareOfSum
```