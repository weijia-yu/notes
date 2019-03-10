# Hoisting


### Execution context

**Global** code – The default envionment where your code is executed for the first time.
**Function** code – Whenever the flow of execution enters a function body.
**Eval code** – Text to be executed inside the internal eval function.

- The JavaScript interpreter in a browser is implemented as a single thread. What this actually means is that only 1 thing can ever happen at one time in the browser
- everytime a function is called, a new execution context is created.

1. **Creation Stage** [when the function is called, but before it executes any code inside]:
- Create the Scope Chain.
- Create variables, functions and arguments.
- Determine the value of "this".


2. **Activation / Code Execution Stage**:
- Assign values, references to functions and interpret / execute code.


1. Find some code to invoke a function.
2. Before executing the function code, create the  `execution context`.
3. Enter the creation stage:
- Initialize the `Scope Chain`.
- Create the variable object:
  - Create the `arguments object`, check the context for parameters, initialize the name and value and create a reference copy.
  - Scan the context for `function declarations`:
    - For each function found, create a property in the  variable object that is the exact function name, which has a reference pointer to the function in memory.
    - If the function name exists already, the reference pointer value will be overwritten.
  - Scan the context for `variable declarations`:
    - For each variable declaration found, create a property in the variable object that is the variable name, and initialize the value as `undefined`.
    - If the variable name already exists in the  variable object, do nothing and continue scanning.
  - Determine the value of "this" inside the context.
4. Activation / Code Execution Stage:
  - Run / interpret the function code in the context and assign variable values as the code is executed line by line.

**function vs variable**

create `function` pointer and assign pointer to the function. Overwritten if function names exists already.

create `variable` and init as undefined. Ignore if the variable name exists already.

## Example

```js
function foo(i) {
    var a = 'hello';
    var b = function privateB() {

    };
    function c() {

    }
}

foo(22);
```