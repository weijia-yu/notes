# Export

### Default Export (export default)

You can have one default export per file. When you import you have to specify a name and import like so:
```js
import MyDefaultExport from "./MyFileWithADefaultExport";
```

### Named Export (export)

With named exports, you can have multiple named exports per file. Then import the specific exports you want surrounded in braces:

```js
// ex. importing multiple exports:
import { MyClass, MyOtherClass } from "./MyClass";
// ex. giving a named import a different name by using "as":
import { MyClass2 as MyClass2Alias } from "./MyClass2";

// use MyClass, MyOtherClass, and MyClass2Alias here
```

