# Intro to Monads

There are several types of monads, but the one I'm interested right now, as I'm still learning about monads, is the Maybe monad (after all, that is how the article about monads on Wikipedia proceeds).

https://en.wikipedia.org/wiki/Monad_(functional_programming)


### Motivation

`Maybe` type is excellent for representing a computation that might fail and we lack the interest to know precisely why it fail, in case it did. For example, a function that might fail does so only for a single reason, so we don't need the resaon spelled out, we already know what it is, we just want to be alerted if that is the case.

This is an extremly important situation in PL desing; it's one of those things that that defines an (elegant) language.

For instance, a function, written in C, that parses a string into a base-10 number, either returns an `int`, or it fails if the input string contains anything other then digits. Being one of the oldest languages, C didn't have too much benefit from a hindsight, so the common way to mark failure is via the *in-band signaling*. The "in-band" part would make sense had it been called "in-type"; that is, signaling error by returning a "special" (in fact, arbitrary) value of the declared return type.

The approach of some OO languages, especially with the chained method calls (where each method inputs what the preceeding shat), there is a constant need for null checks (to avoid null-pointer deref).

Exceptions were another approach to resolve this problem. With exceptions, a function would `throw` an error, and it was up to the calling code to `catch` the error and try to handle it. Such function, that can throw an exception anytime, causes the control to "jump" around at different locations, ruining the chance to reason about the function clearly.


## Maybe type

Using Haskell terminology, the type that can both return the payload or message info, is called `Either`. It has two data constructors: `Right` data ctor carries the payload, while `Left` ctor carries the error info. These ctors are, in a way, just markers of the kind of value that is returned; they tag (flag) the returned value, giving an unambiguous signal wheter the process went fine or not. In case it went fine (determined bypattern matching), you can get at the payload; in case it didn't, you can examine the error.

Less general version of `Either` is `Maybe` type that lightens its size by dropping the error cargo (error information/message). It can still signal a failure only it doesn't haul the specifics around, which can be very convenient at times.


## Maybe type

Undefined values 

are a particularly nasty problem that robust apps need to handle gracefully.

Toward that goal we decided to use the optional type `Maybe`whenever possible



that will mark a value as either carrying a value of some type T (T can be any type) or carrying no value. The new type will be called Maybe T and values of that type can either contain a value of type T, or be the empty value Nothing. A value X of type T which is defined but used in the context of Maybe will be called Just X. This is done to avoid confusion by differentiating between cases where a variable carries a defined value and those where it does not.


So, we decided to use the optional type 

Now that we have switched to optional types, we have a pile of `Maybe Number`


amassed a lot of concrete optional type


For example, we have a function that adds two Maybe Int

the parsing function (the one from C) can now declare `Either Int` as itsreturn type

`Maybe` type is excellent for representing a computation that might fail and we lack the interest to know precisely why it fail, in case it did.

For example, a function that might fail does so only for a single reason, so we don't need the resaon spelled out, we already know what it is, we just want to be alerted if that is the case.
