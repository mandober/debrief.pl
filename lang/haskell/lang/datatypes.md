# Types

- `::` "has the type"
- `=>` type class (constraint), it groups the types by shared props
- `(+) :: Num a => a -> a -> a` 
- plus works for any type, `a`, if it's an instance of the `Num` type class
- multiple type constraints: `(^) :: (Num a, Integral b) => a -> b -> a`
- -> used in type annotations for functions: a -> b -> c
- means func takes value of type `a` and `b` and returns value of type `c`
- -> has right precedence: a -> b -> c is actually a -> (b -> c)
- `() :: ()` unit type that has only one value: `()`
- `IO` is a monad that manages side-effects (print to stdout)
- shared type sig: `(+), (-), (*) :: a -> a -> a`
- use `data` keyword to define a type
- use `class` keyword to define a type class
- use `instance` keyword to implement class' functions



<!-- #region Datatypes -->
# Datatypes

* Concrete datatypes start with capital letter, e.g. `Int`, `Bool`
* Generic types i.e. type params are usually a single letterlowercase, `a`
* Type classes group concrete types by a set of shared properties, `Eq`, `Ord`


**Bool**
- is a boolean type. It can have only two values: True and False.

**Ordering**
- type that can be GT | LT | EQ
- output of `compare` function, e.g. `5 compare 3` -- GT


**Int**
- Int is a bounded integer
- bounded means it has a minimum and a maximum value
- Int is more efficient, but Integer is bigger

**Integer**
- Integer is unbounded integer
- used to represent very big numbers (unbounded), probusing BigInt
- Int is more efficient, but Integer is bigger

**Float**
- single precision floats

**Double**
- double precision floats


**Char**
- character
- denoted by single quotes
- list of characters is String

**String**
- type alias for `[Char]`
- double quotes

*tuple*
- type constructor, `(a, b)`
- hetergenuous
- depends on length and component types
- so theoretically there's an infinite number of tuple types

*unit*
- empty tuple `()` is a unit type
- can only have a single value: `()`

*list*
- `[a]`
- heterogenuous

<!-- #endregion -->


<!-- #region Typeclasses -->

## Typeclasses

**Eq**
- used for types that support equality testing
- functions its members implement are == and /=
- Member types: (), Bool, Char, Ordering, Int, Integer, Float, Double

**Ord**
- is for types that have an ordering, e.g. `(>) :: (Ord a) => a -> a -> Bool`
- All the types we covered so far except for functions are part of Ord
- Ord covers all the standard comparing functions such as >, <, >= and <=
- `compare` func takes two same type Ord members and returns an `Ordering`
- `Ordering` is a type that can be GT, LT or EQ
- To be a member of Ord, a type must first be in `Eq`

**Show**
- Members of Show can be presented as strings
- All types covered so far except for functions are a part of Show
- The most used function that deals with the Show typeclass is `show`
- It takes a value whose type is a Show and presents it as a string

**Read**
- is sort of the opposite typeclass of Show
- `read` function takes a string and returns a type which is a member of Read
- All types covered so far except for functions are a part of Read

**Enum**
- Enum members are sequentially ordered types, they can be enumerated
- tuple, list,
- we can use its types in list ranges
- They have defined successors and predecesors, `succ` and `pred` functions
- Member types: (), Bool, Char, Ordering, Int, Integer, Float, Double

**Bounded**
- members have an upper and a lower bound, `minBound` and `maxBound` funcs
- minBound and maxBound have a type of `(Bounded a) => a`
- In a sense they are polymorphic constants
- members: Bool, Char, Int
- tuples are part of Bounded if the components are also in it

**Num**
- Int, Integer, Double, Float
- Its members have the property of being able to act like numbers
- To be in `Num`, a type must already be in `Show` and `Eq`

**Integral**
- includes Int and Integer
- useful function for dealing with numbers is fromIntegral:
- `fromIntegral :: (Num b, Integral a) => a -> b`

**Floating**
- includes Float and Double

<!-- #endregion -->
