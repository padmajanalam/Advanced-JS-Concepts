# Advanced-JS-Concepts

### Use Strict ###

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
### Different types in Javascript ###

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

### Pass by Value & Pass by Reference ###

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

### What are the different scopes in Javascript? ###
Scope means a life time of a variable.
In Traditional Javascript we have 2 types of Scopes:
* Global Scope
* Functional Scope

* Global Scope - Any a variable declared outside of any function,and they are available in any part of our application.
	* All global variables are actually properties of the Window Object.
	```
	var name = 'Hammad';
	console.log(name); // logs 'Hammad'

	function logName() {
	    console.log(name); // 'name' is accessible here and everywhere else
	}

	logName(); // logs 'Hammad'
	```
* Local/Functional Scope - Decalring a variable inside a function is called a local scope varibales.This will throws an error, if we try to use outside the function.
	```
	function logName() {
	    var test = 1;
	    console.log(test); 
	}

	logName(); // logs 1
	```
* Block Level Scope: In other languages like python or Java we can use a block level scope within the braces.
	* ECMAScript 6 introduced the let and const keywords. These keywords can be used in place of the var keyword.
	```
	if (true) {
		// this 'if' conditional block doesn't create a scope

		// name is in the global scope because of the 'var' keyword
		var name = 'Hammad';
		// likes is in the local scope because of the 'let' keyword
		let likes = 'Coding';
		// skills is in the local scope because of the 'const' keyword
		const skills = 'JavaScript and PHP';
	}

	console.log(name); // logs 'Hammad'
	console.log(likes); // Uncaught ReferenceError: likes is not defined
	console.log(skills); // Uncaught ReferenceError: skills is not defined
	```
* Lexical Scope: Lexical Scope means that in a nested group of functions, the inner functions have access to the variables and other resources of their parent scope.
	```
	function grandfather() {
    		var name = 'Hammad';
   		 // likes is not accessible here
    		function parent() {
      		  // name is accessible here
       		 // likes is not accessible here
       			 function child() {
       		     	  // Innermost level of the scope chain
        	     	  // name is also accessible here
        	    	  var likes = 'Coding';
       	 		}
    		}
	}
	```
* Closures:
	The concept of closures is closely related to Lexical Scope, which we studied above. A Closure is created when an inner function tries to access the scope chain of its outer function meaning the variables outside of the immediate lexical scope. 
	A closure can not only access the variables defined in its outer function but also the arguments of the outer function.

	```
	function greet() {
	    name = 'Hammad';
	    return function () {
		console.log('Hi ' + name);
	    }
	}

	greet(); // nothing happens, no errors

	// the returned function from greet() gets saved in greetLetter
	greetLetter = greet();

	 // calling greetLetter calls the returned function from the greet() function
	greetLetter(); // logs 'Hi Hammad'
	```
	
- One way to call the returned function from the greet function without variable assignment is by using parentheses () two times ()() like this:
	```
	function greet() {
	    name = 'Hammad';
	    return function () {
		console.log('Hi ' + name);
	    }
	}

	greet()(); // logs 'Hi Hammad'
	```




