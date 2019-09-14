# About Haskell

Haskell programming language
* paradigm
  * declarative
  * functional
  * purity, side-effects free
  * referential transparency
* Evaluation strategy
  * lazy evaluation
  * non-strict evaluation
  * call-by-need
* Type system
  * statical typing
  * type inference
  * Hindley-Miner
  * implicitly typed
  * type classes
  * type safety
  * type-safe operator overloading
  * strong type system
* named after logician Haskell Curry
* main implementation: Glasgow Haskell Compiler
* leans on Category theory



Paradigm: Functional

Designed by: Lennart Augustsson, Dave Barton, Brian Boutel, Warren Burton, Joseph Fasel, Kevin Hammond, Ralf Hinze, Paul Hudak, John Hughes, Thomas Johnsson, Mark Jones, Simon Peyton Jones, John Launchbury, Erik Meijer, John Peterson, Alastair Reid, Colin Runciman, Philip Wadler

First appeared: 1990; 29 years ago
Stable release: Haskell 2010 / July 2010; 9 years ago
Preview release: Haskell 2020 announced

Typing discipline: Inferred, static, strong
OS: cross-platform
Filename extensions: .hs, .lhs
Website: www.haskell.org



implicitly typed (types are checked by the compiler, but you don't have to declare them)

* functional (that is, everything is done with function calls)
* statically, implicitly typed (types are checked by the compiler, but you don't have to declare them)
* lazy (nothing is done until it needs to be) language. 






The most common Haskell compiler is GHC. You can download GHC from http://www.haskell.org/ghc/download . GHC binaries are available for GNU/Linux, FreeBSD, MacOS, Windows, and Solaris. Once you've installed GHC, you get two programs you're interested in right now: ghc, and ghci. The first compiles Haskell libraries or applications to binary code. The second is an interpreter that lets you write Haskell code and get feedback right away
