# Features

In addition to support for functions that transform data into other data, the language includes features:

* *Static type checking*: type checking is static, i.e. it is performed at compile-time (as opposed to dynamic that is performed at run-time). Within an adequate editor, type checking is also performed at authoring-time.
* *Strict type checking*: the compiler checks the type of expressions, disallowing operations if the types are not compatible. Naturally. But the strictness here means that implicit type casts and type coercions are either disallowed or reduced to a minimal set of fully documented, well-known and largly expected exemptions (like implicitly coercing an Int into Float).

* *Full type inference*: expressions are fully inferred, so no explicit type annotations by user are required, although they're allowed. Haskell uses *Hindley-Milner* type inference method.

* Higher-order functions, functions as first-class data. Higher-order functions are functions that take other functions as arguments and possibly return functions as values. They are useful for coordinating the work of cooperating functions. Functions themselves are data values. The compiler checks the types of functions just like those of any other data.

* Function-level operators for composing functions. These operators allow the programmer to cleanly glue together functions within a common data path.

* Pattern matching. This provides a means of selecting different computations depending on the structure of the data in a function’s arguments.

* Polymorphic functions. These are functions that provide a single operation on data of different types, such as lists of integers and lists of strings.

* Type classes. A type class provides a set of functions that can be defined differently for different data types belonging to that type class. For example, the function that determines whether one value is less than another must use a
different method for two integers than it does for two strings. The nature and use of all of these features will become clear as you proceed through this book. But before turning to that, this introduction concludes with a brief istory of functional languages and functional programming.


Haskell features:
- lazy evaluation
- lambda expressions
- pattern matching
- list comprehension
- type classes
- type polymorphism

It is a purely functional language, which means that functions generally have no side effects.

A distinct construct exists to represent side effects, orthogonal to the type of functions.

A pure function can return a side effect that is subsequently executed, modeling the impure functions of other languages.


Haskell has a strong, static type system based on Hindley–Milner type inference. Its principal innovation in this area is *type classes*, originally conceived as a principled way to add overloading to the language, but since finding many more uses.

The construct that represents side effects is an example of a monad. *Monads* are a general framework that can model different kinds of computation, including error handling, nondeterminism, parsing and software transactional memory. Monads are defined as ordinary datatypes, but Haskell provides some syntactic sugar for their use.


Haskell has an open, published specification, and multiple implementations exist. Its main implementation, the Glasgow Haskell Compiler (GHC), is both an interpreter and native-code compiler that runs on most platforms. GHC is noted for its rich type system incorporating recent innovations such as generalized algebraic data types and type families. The Computer Language Benchmarks Game also highlights its high-performance implementation of concurrency and parallelism.

An active, growing community exists around the language, and more than 5,400 third-party open-source libraries and tools are available in the online package repository Hackage.
