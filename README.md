# javascript-itself

>*__Wiking__ some concepts in javascript based on my understanding.*

***

## List

>* [TypedArray, ArrayBuffer and View](#typedarray-arraybuffer-and-view)
>* [for...in vs for...of](#forin-vs-forof)
>* [Array.from vs Spread syntax](#arrayfrom-vs-spread-syntax)
>* [Temporal Dead Zone with let, const](#temporal-dead-zone-with-let-const)
>* [Functions](#functions)
>* [Rest parameters](rest-parameters)
>* [Rest parameters(...) vs Spread syntax(...)](#rest-parameters-vs-spread-syntax)
>* ["this" in ES6 Arrow functions](#this-in-es6-arrow-functions)
>* [Iterable in Javascript](#iterable-in-javascript)
>* [Prototype Chaining](#prototype-chaining)
>* [Property access/use declared with/in function](#property-accessuse-declared-within-function)
>* [Default Parameters](#default-parameters)
>* ["this" in Javascript](#this-in-javascript)
>* [Destructuring Assignment](#destructuring-assignment)
>* [Bookmarklet](#bookmarklet)
>* [DOMContentLoaded vs load](#domcontentloaded-vs-load)
>* ["href" attribute in &lt;a&gt;](#href-attribute-in-a)
>* [function*: Generator function](#function-generator-function)

***

### TypedArray, ArrayBuffer and View

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

>__Array.from__ can be used with iterable objects or Array-like objects which don't implement the iterable protocol.  
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

>The __"this"__ value (internally) is not actually bound to the arrow function. Normal functions in JavaScript bind their own __"this"__ value, however the __"this"__ value used in arrow functions is actually fetched lexically from the scope it sits inside. It has no __"this"__, so when you use this you’re talking to the outer scope. *MOST IMPORTANTLY*, __"this"__ in arrow functions only sets once, which means it's pretty static and it never changes.

***

## Iterable in Javascript

>An object is iterable if it defines its iteration behavior, such as what values are looped over in a for...of construct. Some built-in types, such as Array or Map, have a default iteration behavior, while other types (such as Object) do not.  
In order to be __iterable__, an object must implement the __@@iterator__ method, meaning that the object (or one of the objects up its prototype chain) must have a property with a __Symbol.iterator__ key.

***

## Prototype Chaining

>What happens if you call a method on person1, which is actually defined on Object?
```javascript
person1.valueOf()
```
>The browser initially checks to see if the person1 object has a valueOf() method available on it. It doesn't, so the browser then checks to see if the person1 object's __prototype__ object(Person function/class prototype object) has a valueOf() method available on it. It doesn't either, so the browser then checks to see if the Person function/class prototype object's prototype object(Object prototype object) has a valueOf() method available on it. It does, so it is called.

***

## Property access/use declared with/in function

```javascript
function A() {
  var aVar = function() { console.log("local variable"); };
  this.aVar = function() { console.log("member property"); };
}

A.prototype.aVariable = function() { console.log("prototype property"); };
A.aVar = function() { console.log("static property"); };

var a = new A();
a.aVar(); // log: member property
a.aVariable(); // log: prototype property
A.aVar(); // log: static property

// There is no way to access/use the local variable aVar outside of the function A.
```
***

## Default Parameters

>Default function parameters allow formal parameters to be initialized with __default values__ if no value or undefined is passed.

```javascript
function multiply(a, b = 1) {
  return a * b;
}

multiply(5, 2); // 10
multiply(5);    // 5
```

***

## "this" in javascript

>__"this"__ is the current execution context of a function. It varies under the below circumstances:
>- function invocation: global object(window object or undefined in strict-mode)
>- method invocation: the object which contains the method
>- constructor invocation: the newly created object
>- indirect invocation(call, apply, bind): the first argument

***

## Destructuring Assignment

>The __destructuring assignment__ syntax is a JavaScript expression that makes it possible to unpack values from arrays, or properties from objects, into distinct variables.

```javascript
[a, b, ...rest] = [10, 20, 30, 40, 50];
console.log(a); // 10
console.log(b); // 20
console.log(rest); // [30, 40, 50]
```

```javascript
var a = 1;
var b = 3;

[a, b] = [b, a];
console.log(a); // 3
console.log(b); // 1
```

>A variable can be assigned a default, in the case that the value unpacked from the object is undefined.

```javascript
var {a = 10, b = 5} = {a: 3};

console.log(a); // 3
console.log(b); // 5
```

>Setting a function parameter's default value

```javascript
function drawES2015Chart({size = 'big', cords = {x: 0, y: 0}, radius = 25} = {}) {
  console.log(size, cords, radius);
}

drawES2015Chart({
  cords: {x: 18, y: 30},
  radius: 30
});
```
***

## Bookmarklet

>Entering "javascript:" in the url bar executes javascript and it enables us to manipulate the current page.

***

## DOMContentLoaded vs load

>DOMContentLoaded awaits only for HTML and scripts to be loaded.
the load event is fired when the page is fully loaded with all dependent resources including images and styles.

***

## "href" attribute in &lt;a&gt;

>This attribute may be omitted(as of HTML5) to create a placeholder link. A placeholder link resembles a traditional hyperlink, but does not lead anywhere.

***

## function*: Generator function

>The __function*__ declaration defines a __generator__ function. __Generators__ are functions which can be exited and later re-entered. Calling a generator function does not execute its body immediately; an __iterator__ object for the function is returned instead. When the iterator's __next()__ method is called, the generator function's body is executed until the first __yield__ expression. The __next()__ method returns an object with a __value__ property containing the yielded value and a __done__ property which indicates whether the generator has yielded its last value as a boolean. Calling the __next()__ method with an argument will resume the generator function execution, replacing the __yield__ statement where execution was paused with the argument from __next()__. A __return__ statement in a generator, when executed, will make the generator __done__. If a value is __returned__, it will be passed back as the __value__. A generator which has returned will not yield any more values.

```javascript
function* idMaker() {
  var index = 0;
  while (index < 3)
    yield index++;
}

var gen = idMaker();

console.log(gen.next().value); // 0
console.log(gen.next().value); // 1
console.log(gen.next().value); // 2
console.log(gen.next().value); // undefined
```
