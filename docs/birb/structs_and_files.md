---
parent: Birb
nav_order: 3
title: Functions and Structs
---

# Functions and Structs

## Functions

Lambda expressions are not supported so functions must always be constant, which ultimately means that functions can be called above their creation. Although types are implicit, function types must be explicitly defined. A typical function header should look like `nameOfFunc :: {leftParams}.{rightParams} -> {return type} => ()`.
The idea of a left params is so that you can call the function on an input rather than passing the input to the function.

To access the left params you must use the `this` keyword, while the `nest` keyword is used for right params.

If the `leftParams` or return type is omitted, it will be given a `Void` type. To make the rightParams' type `Void` simply put `{}` in place of it. The last expression in a function is the return value implicit, there is no explicit `return`.

Functions can be overloaded, but operators are not yet supported.
```python
/*
 Left Input and void right input
*/
printInt :: {Int}.{} -> {Int} => (
    tweet: this // Prints left parameter
    this        // Returns the left parameter
)

10.printInt     // Prints 10

/*
    Named right parameters
*/
addNums :: {num1 => Int, num2 => Int} -> {Int} => (
    result => nest.num1 + nest.num2     // Creates a variable (result) with the value of num1 + num 2
    result      // Returns result
)

tweet => addNums => 10, 5   // Prints 15

/*
 Nothing Specified
*/
printHenlo :: {} => (
	tweet => "Henlo"
)

printHenlo // prints Henlo
```

The result of the code above would be:
```
10
15
Henlo
```

## Structs

Structs are also constant, hence they must be declared with `::`. 
```
type :: {String, Int} // Commas are only for readability, any whitespace is fine too

// OR NAMED

type :: {strElement => String, intElement => Int}

// Constructor
constructorMethod :: {param1 => Int, param2 => Int} -> {type} =>
(
    nest.param1, nest.param2
)

// Function for type struct
print :: {type} =>
(
	tweet: nest.foo.String + ", " + nest.bar.String
)

```

Unnamed elements will be named alphabetically, `a, b, c, d ...`.