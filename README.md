# Advanced-JS-Concepts

### Use Strict ###

- Strict mode allows us to place a program or a function in strict operating context.
- It is like a string format "use string".
- It will support modern browsers only and older browsers will ignore the strict mode as it is in string format.
- Anything under the strict mode will follow and throws erros accordingly and out-side the code will follow non strict mode.

```
“use strict”;
Var theVal = 0;

thVal = 1;

if(theVal > 0){
	console.log(“Test”);
}

O/P : this will throws an error : thVal is not defined.
```
