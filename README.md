# Advanced-JS-Concepts

#### Use Strict ####

- Strict mode is a new feature in ECMAScript5 and it allows us to place a program or a function in strict operating context.
- It will support modern browsers only and older browsers will ignore the strict mode as it is in string format and consider it as a string.
- Anything under the strict mode will follow and throws erros accordingly and out-side the code will follow non strict mode.
- We can use strict mode in 2 ways, by using in global scope for entire script and by using for individual functions.
- In strict mode we can't use variables that have not been declared with var first.
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

- Non - strict mode: 

```
eval(“var a=1”);
console.log(a); 

O/P :  it will evaluate eval and give a value as 1
```
- Strict Mode:

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
#### Different types in Javascript ####

There are two different data types:
* Primitive data type
	* There are **five types** of primitive data types in JavaScript.
		* String		// 'JOHN'
		* Number		// 22
		* Boolean		// true
		* Null			// null
		* Undefined.		// undefined
* Non - Primitive data type 
	* Objects (Arrays comes under object).	// new Object()

To find the type of a variable we have a javascript function **typeof**.
* typeof(1)		// Number
* typeof('test')	// string
* typeof(true) 		// Boolean
* typeof(undefined)	// undefined
* typeof(null)		// Object -> incorrectly js reported it as Object which supposed to be a null.
* typeof({})		// Object
* typeof([])		// Object

As Javascript is a `dynamic type language` we dont have to mention the data type at the time of variable declaration.

	* String x = 'test' // Wrong. No need to specify the type here.
By Javascript, we can change the type of the variable dynamically at run time.

#### Pass by Value & Pass by Reference ####

Before understanding pass by value and pas by reference,we must know the javascript datatypes ^.

**Pass by Value:**
- Primitive type variable like string,number are always pass as pass by value.	
- If we change the value of a primitive type inside a function, the changes won't effect the varibale in the outer scope.
- pass by value means passing the `copy of a variable`.
```
// global varable - outer scope
var a = 1; // primitive type - Number
function test(a){
	// inner scope
	a = 2;	
	console.log(a); // O/P : 2

}
test(a);	// O/P : 1
console.log(a); // O/P : 1

```
**Pass by reference:**
- Javascript passing in an object passes it by reference.When we change the property of the object, then the change will be reflected in the outer scope.

```
var ref = {};
function test(ref){
	ref.foo = false;
}
test(ref);
console.log(ref); // O/P: Object {foo:false}
```

```
var ref = {"course":"JS"};
function test(ref){
	// not a reference, simlpy a value re-assigning.
	ref = {"JS":"Course"};	
	// we can only change the property of the variable passed to the function.
}
test(ref);
console.log(ref); // O/P: Object {"course":"JS"} accepts the outer scope variable value.
```
**Practice: What will be the output?**

```
"use strict";
var a = 1;
var b = {};
function foo(x, y) {
  x = 2;
  y.moo = 3;
}
 
foo(a, b);
console.log("a = " + a + "; b = " + JSON.stringify(b));
```
