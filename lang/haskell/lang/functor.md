# Functor

- `Functor` typeclass is a generalization of a mappable container type.
- Functor's instances are types that are mappable.
- Functor class collects types that can act as containers
- types that can be mapped: [a], (a), Maybe a

>:t Functor
class Functor (f :: * -> *) where
  fmap :: (a -> b) -> f a -> f b
  (<$) :: a -> f b -> f a
  instance Functor (Either a)
  instance Functor []
  instance Functor Maybe
  instance Functor IO
  instance Functor ((->) r)
  instance Functor ((,) a)

Functor class prototypes 2 funcs: `fmap` and `<$`

The sig of fmap is: `fmap :: (a -> b) -> f a -> f b`

> f is a type constructor that takes one type parameter.

In the definitions of typeclasses seen so far, the type variable that played
the role of the type in the typeclass was a *complete type*, like `a` here:
    `(==) :: (Eq a) => a -> a -> Bool`
which means the class `Eq` is parameterized over a concerte type, `a`. When we fill a concrete type in for the `a` param it becomes complete.

But in fmap, `f` is a type parameter but due to it being juxtaposed with another type param `a`, means that the `f` is not a concrete type parameter but a type constructor. And type ctors are functions - that's why it has the letter `f` (as a mnemonic only, it is arbitrary letter).

A type CTOR takes a type param and constructs the concrete type (i.e. a value of concrete type). Type ctors may be parameterless, or they may take 1 (most common) or more type params.



- 42    :: Int
- 42    ∈ Int
- value ∈ type
- type  ∈ class
- Int   ∈ Num
- Num = {Int,Integer,Float,Double}
- Integral = {Int,Integer}
- Floating = {Float,Double}
- Integral ⊆ Num
- Floating ⊆ Num
- some values are constructed using their value ctor (type ctor):
- False ∈ Bool
- False is a Boolean value, but it is also a parameterless value/type ctor
- Other value ctors take type params: (a), [a], Maybe a
- list with elem has a type, but even the empty list has a type

- <valCtor> <type>
- Right     a
- Left      b
- Just      a
- Nothing       (no type param)
- []        a   (list is parameterized over the type of its elements)
- f         a   (ctor type param that takes 1 type param)


- value, x
- ctor, f (because ctors are functions)
- ctor type, f a
- type, a
- class, τ (Num, Eq)



does not stand for is not a complete type (it's not a type that a value can hold like `Int`, `Bool`, `Maybe String`, etc.) but it's a *type constructor* that takes one *type parameter*.

So `fmap` takes a function `a -> b` and a


`Maybe Int` is a concrete type, but `Maybe` is a type constructor that takes one type as the parameter.

We see that fmap takes a function from one type to another and a functor applied with one type and returns a functor applied with another type.



class Mappable f where
    mapper :: (a -> b) -> f a -> f b
    -- f is a type constructor taking 1 type param

-- list is a functor:
instance Mappable [] where
    mapper = map


{-  Notice we didn't write:
        instance Functor [a] where

    because from
        fmap :: (a -> b) -> f a -> f b

    we see that f has to be a type constructor that takes one type.
    [a] is already a concrete type (of a list with any type inside it),
    while [] is a type constructor that takes one type and produces types
    such as [Int], [String], [[String]], etc.

    What happens when we map or fmap over an empty list?
    we get an empty list. It just turns an empty list of
    type [a] into an empty list of type [b].

    Types that can act like a box can be functors.
    Maybe is like a box that can either hold nothing, so it has value of Nothing, or it can hold one item, like "HAHA", in which case it has
    a value of Just "HAHA".

    Maybe is a functor:
-}
instance Mappable Maybe where
    mapper f (Just x) = Just (f x)
    mapper f Nothing = Nothing
