# This


### Why we need this

this is used inside a function (let’s say function A) and it contains the value of the object that invokes function A. We need this to access methods and properties of the object that invokes function A, especially since we don’t always know the name of the invoking object,



- Whenever you use the keyword “this” in the global context (not inside a function), it always refers to the global object.

- The object that “this” refers changes every time execution context is changed.
- When a function is invoked with “new” keyword then the function is known as constructor function and returns a new instance. In such cases, the value of “this” refers to newly created instance.

- this is not assigned a value until an object invokes the function where this is defined.


### The this keyword is most misunderstood when we borrow a method that uses this


+ When a function is invoked with “new” keyword then the function is known as constructor function and returns a new instance.
+ In Javascript, property of an object can be a method or a simple value. When an Object’s method is invoked then “this” refers to the object which contains the method being invoked.

```js
function foo () {
	'use strict';
	console.log("Simple function call")
	console.log(this === window); 
}

let user = {
	count: 10,
	foo: foo,
	foo1: function() {
		console.log(this === window);
	}
}

user.foo()  // Prints false because now “this” refers to user object instead of global object.
let fun1 = user.foo1;
fun1() // Prints true as this method is invoked as a simple function.
user.foo1()  // Prints false on console as foo1 is invoked as a object’s method```

