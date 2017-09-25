# javascript-itself

>*__Wiking__ some concepts in javascript based on my understanding.*

***

## List

>* [TypedArray, ArrayBuffer and view](#typedarray-arraybuffer-and-view)
>* [for...in vs for...of](#forin-vs-forof)
>* [Array.from vs Spread syntax](#arrayfrom-vs-spread-syntax)
>* [Temporal Dead Zone with let, const](#temporal-dead-zone-with-let-const)
>* [Functions](#functions)
>* [Rest parameters](rest-parameters)
>* [Rest parameters(...) vs Spread syntax(...)](#rest-parameters-vs-spread-syntax)
>* ["this" in ES6 Arrow functions](#this-in-es6-arrow-functions)

***

### TypedArray, ArrayBuffer and view

>__TypedArray__ consists of buffer(ArrayBuffer) + view.  
>__Arraybuffer__ is an actual strorage for the bytes which is used for binary data transfers between server and client.  
>You need __View__ to access the content of __Arraybuffer__.  
[More Information](https://stackoverflow.com/questions/42416783/where-to-use-arraybuffer-vs-typed-array-in-javascript)

***

### for...in vs for...of

>__for...in__ only iterates __enumerable__ properties including prototype chain.  
>__for...of__ only works with iterable objects such as Array, String.

***

### Array.from vs Spread Syntax

>__Array.from__ can be used with Array-like objects or iterable objects.  
>__Spread syntax(...)__ (other than in the case of spread properties) can be only used with iterable objects.

***

## Temporal Dead Zone with let, const

>In ECMAScript 2015, __let__ bindings are not subject to __Variable Hoisting__, which means that __let__ declarations do not move to the top of the current execution context. Referencing the variable in the block before the initialization results in a __ReferenceError__ (contrary to a variable declared with var, which will just have the undefined value). The variable is in a __"temporal dead zone"__ from the start of the block until the initialization is processed.

***

## Functions

>In JavaScript, functions are first-class objects, because they can have properties and methods just like any other object. What distinguishes them from other objects is that functions can be called. In brief, they are __Function__ objects.

***

## Rest parameters

>function f(a, b, ...theArgs) {}  
If the last named argument of a function is prefixed with ..., it becomes an __array__ whose elements from 0 (inclusive) to theArgs.length (exclusive) are supplied by the actual arguments passed to the function.

***

## Rest parameters(...) vs Spread syntax

>__Rest syntax__ is the opposite of __Spread syntax__: __Spread__ 'expands' an array into its elements, while __Rest__ collects multiple elements and 'condenses' them into a single element.

***

## "this" in ES6 Arrow functions

>The __this__ value (internally) is not actually bound to the arrow function. Normal functions in JavaScript bind their own __this__ value, however the __this__ value used in arrow functions is actually fetched lexically from the scope it sits inside. It has no __this__, so when you use this you’re talking to the outer scope.
