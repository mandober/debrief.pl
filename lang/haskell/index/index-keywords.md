# Keywords

Reserved Words (always)
- module, newtype, type, class, instance, data
- deriving, import, where
- do, let, in, of
- if, then, else, case
- infix, infixl, infixr

Reserved Words (with certain ext or implementations)
- `forall` (GHC) reserved keyword at the type level, contrary to the Haskell Report, which allows type variables to be named forall
- foreign


Types:
- Bool, Ordering, Char, String
- Int, Integer, Float, Double
- ()

Typeclasses:
* Num (a => where a is: Int, Integer, Float, Double)
  * Integral (a => where a is: Int, Integer)
    * Bounded (a => where a is: Int, Bool, Char)
  * Floating (a => where a is: Float, Double)


`data`, `type`, `newtype`, `class`, `instance`, `deriving`, `foreign`.

Top-level declarations:
- `data`
- `type`
- `newtype`
- `class`, `instance`
- `deriving`
- `foreign`
