# new keyword 

1. It creates a new object. The type of this object is simply object.
2. It sets this new object's internal, inaccessible, [[prototype]] (i.e. __proto__) property to be the constructor function's external, accessible, prototype object (every function object automatically has a prototype property).
3. It makes the this variable point to the newly created object.
4. It executes the constructor function, using the newly created object whenever this is mentioned.
5. It returns the newly created object, unless the constructor function returns a non-null object reference. In this case, that object reference is returned instead.

### prototype

Every object (including functions) has this internal property called [[prototype]]. It can only be set at object creation time, either with new, with Object.create, or based on the literal (functions default to Function.prototype, numbers to Number.prototype, etc.). It can only be read with Object.getPrototypeOf(someObject). There is no other way to set or read this value.

Functions, in addition to the hidden [[prototype]] property, also have a property called prototype, and it is this that you can access, and modify, to provide inherited properties and methods for the objects you make.