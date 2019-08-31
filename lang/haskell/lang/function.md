# Functions

- A function has input and output
- it describes how to produce the output from its input
- Functions can be applied, which means that you give an input value as arg to the function and then expect to receive the corresponding output value.
- Haskell functions are first class entities, they
  - can be given names (can be bound to identifiers)
  - can be the value of some expression
  - can be members of a list
  - can be elements of a tuple
  - can be passed as parameters to a function
  - can be returned from a function as a result



<!-- #region Functions -->

In ghci use `let`, but not in source file.
> let triple x = x * 3

In a source file, def a func like this:
```hs
triple x = x * 3
```
Func name must be lowercase.

Apply a func to the arg:

```hs
triple 4
```

The expression `triple 4` is a *redex*, it is an expr in *canonical or normal form* when it reaches the number 12 (because the value 12 cannot be reduced further).


## Infix operators
Func default to being in prefix position. You can sometimes use functions in an infix or prefix style by wrapping its name in acute quotes.
> div 10 4
> 10 `div` 4

<!-- #endregion -->

## Associativity and precedence
<!-- #region Associativity -->
When you ask GHCi for the :info about an operator or function, it provides the type information and tells you whether it's an infix operator with precedence.

> :info (*)
infixl 7 *

- infixl means infix operator, left associative
- 7 is the precedence: higher is applied first, on a scale of 0-9.

infixl is left-ass so    
> 2 * 3 * 4    
is the same as     
> (2 * 3) * 4


Comma is used to assign left-associativity and precedence (6) for an inquiry about addition and subtraction operators:
> :info (+) (-)
infixl 6 +, -

Exponentiation associate to the right, but it is not associative and thus makes a prime candidate for demonstrating left vs. *right-associativity*:

> :info (^)
infixr 8 ^

> 2 ^ 3 ^ 4
is eval as
> 2 ^ (3 ^ 4)


> 2 ^ 3 ^ 4
2417851639229258349412352
> 2 ^ (3 ^ 4)
2417851639229258349412352
> (2 ^ 3) ^ 4
4096
<!-- #endregion -->


## Partial application
<!-- #region Sectioning -->

https://wiki.haskell.org/Partial_application

motto: **Functions are not partial, but you can partially apply a function**

Partial application in Haskell involves passing less than the full number of arguments to a function that takes multiple arguments.

```hs
add :: Int -> Int -> Int
add x y = x + y
addOne = add 1
```

The `->` operator is right associative, and function application is left associative, meaning the type signature of `add` actually looks like this:

```hs
add :: Int -> Int -> Int
-- The `->` operator is right associative:
add :: Int -> (Int -> Int)

add 5 3
-- function application is left associative:
(add 5) 3
```
This means that add actually takes one argument and returns a function that takes another argument and returns an Int.


### Example with composition

```hs

-- comp2 is binary func taking 2 args f g, returning z
-- comp2 :: f -> g -> z
-- comp2 :: f -> (g -> z)
--    f :: (a -> b)         unary
--    g :: (b -> b -> c)    binary
--out z :: (a -> a -> c)    binary

comp2 :: (a -> b) -> (b -> b -> c) -> (a -> a -> c)
comp2 f g = (\x y -> g (f x) (f y))

-- is this a partial definition of comp2'
comp2' f = (\x y -> add (f x) (f y))

-- not really, this is another func, but to get
-- the desired result just partially apply comp2:
comp2' f = comp2 f add
```





## Sectioning
Sectioning allows you to pass around partially-applied functions. With commutative functions, such as addition, it makes no difference if you use (+1) or (1+) because the order of the arguments won’t change the result. If you use sectioning with a function that is not commutative, the order matters.

Subtraction, (-), is a special case. Enclosing a value inside the parentheses with the minus indicates to GHCi that it’s the argument of a function. Because the minus function represents *negation*, not *subtraction*, when it’s applied to a single argument, GHCi does not know what to do with that, and so it returns an error message. Here, minus is a case of syntactic overloading disambiguated by how it is used.


```hs
(+1) 3 -- 4
(3+) 5 -- 8

(/2) 1 -- 0.5
(2/) 1 -- 2

2 - 1 -- 1
(-) 2 1 -- 1
(-2) 1 -- error
```

To use sectioning for subtraction, only the first argument may be partially applied:
> let x = 5
> let y = (1 -)
> y x
-4


## HOF
A higher-order function is a function that takes other functions as arguments or returns a function as result.

Two other common ones are curry, uncurry. A possible implementation of these is:

curry :: ((a,b)->c) -> a->b->c
curry f a b = f (a,b)

uncurry :: (a->b->c) -> ((a,b)->c)
uncurry f (a,b)= f a b


<!-- #endregion -->



## Laws for quotients and remainders

<!-- #region Laws -->

The quot/rem, div/mod class methods satisfy these laws if y is non-zero:

```hs
(x `quot` y)*y + (x `rem` y) == x
(x `div`  y)*y + (x `mod` y) == x
```

* `quot` is integer division truncated toward zero
* `div` is integer division truncated toward negative infinity

The `div` function is often the more natural one to use, whereas the `quot` function corresponds to the machine instruction on modern machines, so it's somewhat more efficient.


## Lambdas
The lambdas beneath let expressions

Anonymous function syntax in Haskell uses a backslash to represent a lambda.

```hs
-- abstraction
(\x -> x)

-- application
(\x -> x) 0
```

In ghci use `let`
> let id = \x -> x
> id 1
1

or define a func like this:
> let id x = x
> id 4
4

## From let to lambda

```hs
let a = b in c
-- means: bind b to a in the expr c
-- so in lamnda expr, b is arg, a is param, and
-- c is lambda body, which is here just a
(\a -> a) b

let x = 10 in x + 9001
(\x -> x + 9001) 10
```


## From where to lambda

We can do a similar translation with where, although there are minute fifferences that we will not address. 

again, a is param, b is arg and c is the body.


```hs
c where a = b
(\a -> a) b

-- so:
let x = 10 in x + 9001
-- is eq:
identifier = x + 9001
   where x = 10
-- is eq:
(\x -> x + 9001) 10
```


```hs
let x = 3; y = 1000 in x * 3 + y
op1 = x * 3 + y where
  x = 3
  y = 1000

let y = 10; x = 10 * 5 + y in x * 5
op2 = x * 5 where
  y = 10
  x = 10 * 5 + y

let x = 7; y = negate x; z = y * 10 in z / x + y
op3 = z / x + y where
  x = 7
  y = negate x
  z = y * 10
```

<!-- #endregion -->


## The $ operator

The dollar operator is defined as an infix operator with the lowest possible precedence:

> :info ($)
($) :: (a -> b) -> a -> b
infixr 0 $

The ($) operator is a convenience for when you want to express something with fewer parentheses:

> (2^) $ 2 + 2
16
> (2^) (2 + 2)
16

*Evaluate everything to the right of ($) first*.

    f      g      x
> (2^) $ (+2) $ 3 * 2
  (2^) $ (+2) 6
  (2^) 8
  256

but:

    f      g  x1  x2
> (2^) $ (+2) 3 * 2 
  (2^) $  5     * 2
  (2^) 10
  1024
  
Function application has precedence over mult.


> (2^) $ 2 + 2 $ (*30)
A rather long and ugly type error about trying to
use numbers as if they were functions follows.
