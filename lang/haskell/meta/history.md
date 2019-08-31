# Meta

https://github.com/bitemyapp/learnhaskell

- 1990 Haskell v.1
- 1999 Haskell 98 standard published
- 2010 Haskell 2010 standard published (adds FFI)

Features
- functional: data flows through functions
- pure: functions are pure, without side-effects
- lazy: evaluation strategy is call-by-need
- type system: static, strong, Hindley-Miner

GHC Haskell Components:
- ghc       Compiler
- ghci      Interpreter
- runghc    For running scripts
- ghc-pkg   Package manager, e.g. `ghc-pkg list` Show installed pkgs


## The Haskell Programming Language

Haskell is named after the mathematician and logician Haskell Curry (1900-1982).

The principal ideas and the design of the language were the work of a committee that met at a conference on functional programming in 1987, and the first definition of the language was released in 1990.

The committee believed that the most useful aspects of various functional languages should be consolidated into a single standard, and Haskell was the result.

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
