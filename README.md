# Advanced-JS-Concepts

### Use Strict ###

- Strict mode allows us to place a program or a function in strict operating context.
- It is like a string format "use strict".
- It will support modern browsers only and older browsers will ignore the strict mode as it is in string format and consider it as a string.
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

- We cannot delete variable values or functions when we are in strict mode.
- And Strict mode will not allow us to delete arguments of a function too.

```
“use strict ”;

Var foo =1;
Delete foo;

function test(){}
delete test;

O/P : Throws an error : Delete of an unqualified identifier in strict mode
```

- Eval functions are safer with in the strict mode and it won’t evaluate the eval block.

*  Non - strict mode: 

```
eval(“var a=1”);
console.log(a); 

O/P :  it will evaluate eval and give a value as 1
```
* Strict Mode:

```
“use strict ”;

eval(“var a=1”);
console.log(a);  

O/P: will throws an error a is not defined.
```

```
“use strict ”;

Var a = 2;
eval(“var a=1”);
console.log(a); 

O/P : returns 2 as eval is not evaluated because of strict mode

```


