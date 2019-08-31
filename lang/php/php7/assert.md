# Assertions

http://php.net/manual/en/function.assert.php

`assert()` is a language construct in PHP 7, allowing for the definition of assertions that take effect in development and testing environments, but get removed in production.

While `assert_options()` can still be used to control behaviour as described above for backward compatibility reasons, PHP 7 only code should use the two new configuration directives to control the behaviour of `assert()` and not call `assert_options()`.

PHP 7 configuration directives:
* `zend.assertions`
  * 1: generate and execute code (development mode) *default*
  * 0: generate code but jump around it at runtime
  * -1: do not generate code (production mode)
* `assert.exception`
  - 1: throw when the assertion fails, either by throwing the object provided as the exception or by throwing a new `AssertionError` object if exception wasn't provided
  - 0: use or generate a `Throwable`, but only generate a warning based on that object rather than throwing it (PHP 5 compatible) *default*
