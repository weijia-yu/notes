# Immediately-invoked Function Expression

+ we are prefixing “!” in-front of the function keyword on line 1. This basically enforces JavaScript to treat whatever that’s coming after “!” as an expression.

+ The above stylistic variation can be used by replacing “!” with “+”, “-”, or even “~” as well. Basically any unary operator can be used.
+ void is basically forcing the function to be treated as an expression.

+ wrapped in parentheses


Take parameter:

IIFEs with parameters

Not only IIFEs can return values, but IIFEs can also take arguments while they are invoked. Let’s see a quick example.

```js
(function IIFE(msg, times) {
    for (var i = 1; i <= times; i++) {
        console.log(msg);
    }
}("Hello!", 5));```