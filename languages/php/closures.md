<?php

# CLOSURES

/*
You may be familiar with JavaScript closures, where you can simply use any variable 
from the outside scope without doing anything particular. In PHP, you need to use 
the `use` keyword to import an existing variable into the scope of an anonymous function:
*/
$some_variable = 'value';

$my_closure = function() use($some_variable)
{
  //
};

// PHP closures use an EARLY-BINDING approach. 
// This means that the variable inside the closure will have the value that the 
// variable had at the CLOSURE CREATION. If you change the variable afterward, the 
// change will not be seen from inside the closure:
$s = 'orange';
$my_closure = function() use($s) { echo $s; };
$my_closure(); // display 'orange'
$s = 'banana';
$my_closure(); // still display 'orange'

// You could pass the variable by REFERENCE so that changes to the variable are 
// propagated inside the closure
$my_closure2 = function() use(&$s) { echo $s; };
$my_closure2(); // banana
$s = 'kiwi';
$my_closure2(); // kiwi


# CLOSURES OVER OBJECTS

// Be aware that when you pass objects to a closure, any modification done to 
// properties in the object will be accessible inside the closure. PHP does not make
// a copy of objects when passed to the closure.


# CLOSURES INSIDE OF CLASSES

// If you declare any anonymous function inside a class, it will automatically get
// access to the instance reference via the usual $this variable. To stay coherent
// about the vocabulary, the function will automatically become a closure:
class ClosureInsideClass
{
    public function testing()
    {
        return function() {
            var_dump($this);
        };
    }
}

$object = new ClosureInsideClass();
$test = $object->testing();
$test();

// If you want to avoid this automatic binding, you can declare a static anonymous function:
class ClosureInsideClass
{
    public function testing()
    {
        return (static function() {
            // no access to $this here, the following line will result in an error.
            var_dump($this);
        });
    }
};

$object = new ClosureInsideClass();
$test = $object->testing();
$test();



# USING OBJECTS AS FUNCTIONS

// Sometimes, you might want to split your function into smaller parts, but without
// those parts being accessible to everyone. When this is the case, you can leverage
// the __invoke magic method on any object that let you use an instance as a function
// and hide that helper function as private methods inside your object:
class ObjectAsFunction
{
    private function helper(int $a, int $b): int
    {
        return $a + $b;
    }

    public function __invoke(int $a, int $b): int
    {
      return $this->helper($a, $b);
    }
}

$instance = new ObjectAsFunction();
echo $instance(5, 10);

// The __invoke method will be called with any parameters you pass to the instance. 
// If you want, you can also add a constructor to your object and use any methods 
// and properties that it contains. Just try to keep it as pure as possible, because 
// as soon as you use mutable properties, your function will be harder to understand.


# THE CLOSURE CLASS

/*
All anonymous functions are in fact an instance of the Closure class. However, as 
stated in the documentation (http://php.net/manual/en/class.closure.php), this class 
does not use the aforementioned __invoke method; it's a special case in the 
PHP interpreter:
  "Besides the methods listed here, this class also has an __invoke method. This is 
  for consistency with other classes that implement calling magic, as this method is
  not used for calling the function."

This method on the class allows you to change to which object the $this variable will
be bound inside the closure. You can even bind an object to a closure created outside 
of the class.

If you start using the features of the Closure class, keep in mind that the call 
method was just recently added in PHP 7.
*/


# CALLABLE 
/*
callable is a type hint that can be used to enforce that the parameter of a function 
is something that can be called, like a function. Beginning with PHP 7, it can also 
be used as a type hint for the return value:
*/

function test_callable(callable $callback) : callable {
    $callback();
    return function() {
        // [...]
    };
}

/* However, what you cannot enforce with the type hint is the number and type of 
arguments your callable should have. But it is already great to guarantee to have 
something you can call.

A callable can take multiple forms:
- A string for named functions
- An array for class methods or static functions
- A variable for anonymous functions or closures
- An object with a __invoke method


Let's start with calling a simple function by name:
*/
$callback = 'strtoupper';
$callback('Hello World !');


/* We can also do the same for functions inside of classes. 
Let's declare an A class with some functions and use an array to call it. */
class A {
    static function hello($name) { 
        return "Hello $name !\n"; 
    }
    
    function __invoke($name) { 
        return self::hello($name); 
    }
}
// array with class name and static method name
$callback = ['A', 'hello'];
$callback('World');

/* Using a string will only work for the static method, as other methods will need 
an object to use as their context. In the case of a static method, you can also use 
a simple string directly, this will, however, only work starting with PHP 7; 
the previous version didn't support this syntax:
*/
$callback = 'A::hello';
$callback('World');

// You can call a method on a class instance as easily:
$a = new A();
$callback = [$a, 'hello'];
$callback('World');

// Since our A class has an __invoke method, we can use it as a callable directly:
$callback = $a;
$callback('World');

// You can also use any variable to which an anonymous function is assigned as a callable:
$callback = function(string s) {
    return "Hello $s !\n";
}
$callback('World');

/* 
PHP also provides you with two helpers to call functions in the form of 
call_user_func_array and call_user_func. 
They take a callable as a parameter and you can also pass parameters. 
For the first helper, you pass an array with all the parameters; 
for the second one, you pass them separately:
*/
call_user_func_array($callback, ['World']);

/*
A final word of caution, if you are using the callable type hint: any string that 
contains a function name that has been declared is considered valid; this can lead 
to some unexpected behavior sometimes.

A somewhat contrived example would be a test suite where you check that some functions
only accept valid callables by passing it some strings and catching the resulting 
exception. At some point, you introduce a library and this test is now failing, 
although both should be unrelated. What is happening is that the library in question 
declares a function with the exact name that your string contained. Now, the function 
exists and no exception is raised anymore. */























