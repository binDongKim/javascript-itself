# javascript-itself

>*__Wiking__ some concepts in javascript based on my understanding.*

***

## List

>* [TypedArray, ArrayBuffer and view](#typedarray-arraybuffer-and-view)
>* [for...in vs for...of](#forin-vs-forof)
>* [Array.from vs Spread syntax](#arrayfrom-vs-spread-syntax)
>* [Temporal Dead Zone with let, const](#temporal-dead-zone-with-let-const)

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
>__Spread syntax(...)__ can be only used with iterable objects.

***

## Temporal Dead Zone with let, const

>In ECMAScript 2015, let bindings are not subject to Variable Hoisting, which means that let declarations do not move to the top of the current execution context. Referencing the variable in the block before the initialization results in a ReferenceError (contrary to a variable declared with var, which will just have the undefined value). The variable is in a "temporal dead zone" from the start of the block until the initialization is processed.
