# ES6 - Javascript Concepts

## Array Helper Methods ##

* ForEach
* Map
* Filter
* Find
* Every
* Some
* Reduce

### Foreach ###

The forEach() method executes a provided function once for each array element.We can pass the anonymous callback to the forEach and we cna pass a reference of the function to the forEach as well.

```
var colors = ['blue', 'green', 'yellow'];
colors.forEach(function(color){
  console.log(color); // blue , green, yellow
})
```

```
Sum of Array items:
var numbers = [1,2,3,4,5];
var sum = 0;

numbers.forEach(function(number){
  sum += number;
});
console.log(sum); // 15
```
```
var images = [
  { height: 10, width: 30 },
  { height: 20, width: 90 },
  { height: 54, width: 32 }
];
var areas = [];

images.forEach(function(image){
    areas.push(image.height * image.width);
})

console.log(areas);//Area of images
```
### MAP ###

arr.map() function creates a new array with the results of called function for every array element. 

The map() method creates a `new array` with the results of calling a provided function on every element in the calling array.
make sure return the array in Map method.

```
var numbers = [1,2,3,4,5];
var doubleValue = numbers.map(function(number){
  return number * 2;
});

console.log(doubleValue); // (5) [2 ,4 ,6 ,8 ,10]
```
=> Pluck - Array objects
```
var cars = [
{model: 'Benz', price: 'Expensive'},
{model: 'Maruthi', price: 'Cheap'},
];

var prices = cars.map(function(car){
  return car.price;
});

console.log(prices); // ['Expensive', 'Cheap']
```
```
var images = [
  { height: '34px', width: '39px' },
  { height: '54px', width: '19px' },
  { height: '83px', width: '75px' },
];

var heights = images.map(function(image){
    return image.height;
});
console.log(heights);
```
```
var trips = [
  { distance: 34, time: 10 },
  { distance: 90, time: 50 },
  { distance: 59, time: 25 }
];

var speeds = trips.map(function(trip){
    return trip.distance / trip.time;
});
console.log(speeds);
```
### Filter ###
arr.filter() is used to create a new array function and this function returns a new array consisting of only those elements that satisfied the `condition of the function`.
The filter() method creates a new array with all elements that pass the test implemented by the provided function.

```
var words = ['spray', 'limit', 'elite', 'exuberant', 'destruction', 'present'];
const result = words.filter(word => word.length > 6);
console.log(result);
// expected output: Array ["exuberant", "destruction", "present"]
```
```
var products = [
  { name: "apple", type:'fruit', quantity:0, price:1},
  { name: "Tomato", type:'Veg', quantity:10, price:15},
  { name: "Melon", type:'fruit', quantity:20, price:20},
  { name: "Brinjal", type:'Veg', quantity:5, price:10},
  { name: "Banana", type:'fruit', quantity:5, price:16},
  { name: "Grapes", type:'fruit', quantity:15, price:45},
  { name: "Capsicum", type:'Veg', quantity:3, price:9},
  ];
  
var res =   products.filter(function(product){
    return product.type === 'fruit' && product.quantity >0 && product.price <= 20 
})
  
console.log(res); // returns fruit where quantity > 0 and price < 20.
```
#### Relational data ####
```
var post = {id:4, title: "New Post"};
var comments = [
  {id:1, postID:4,comment:"test1"},
  {id:2, postID:3,comment:"test post 3"},
  {id:3, postID:4,comment:"test post 4"},
  ];
function postComment(comments,post){  
  return comments.filter(function(comment){
    return comment.postID == post.id
  });
}
console.log(postComment(comments,post));
```
```
var numbers = [15, 25, 35, 45, 55, 65, 75, 85, 95];
var filteredNumbers = numbers.filter(function(number){
    return number >50
});
console.log(filteredNumbers);
```
```
var users = [
 { id: 1, admin: true },  
 { id: 2, admin: false },
 { id: 3, admin: false },
 { id: 4, admin: false },
 { id: 5, admin: true },
];

var filteredUsers = users.filter(function(user){
    return user.admin === true
});

console.log(filteredUsers);
```
```
=> to fetch the opposite of the condtion using filter

var numbers = [10,20,30];
var lessthan = reject(numbers,function(number){
  return number > 15;
});

function reject(array, iteratorFunction) {
 return array.filter(e => !iteratorFunction(e));
}

console.log(lessthan);  // [10]
```
### Find ###

The find() method returns the value of the first element in the array that satisfies the provided testing function. Otherwise undefined is returned.

```
var array1 = [5, 12, 8, 130, 44];

var found = array1.find(function(element) {
  return element > 10;
});

console.log(found);
// expected output: 12
```

```
var names = [
  {name : 'Zil'},
  {name : 'Bill'},
  {name : 'Alex'}
  ];
  
  var test = names.find(function(x){
    return x.name === 'Alex';
  })
  
console.log(test);
```
```
var posts = [
  {id:4, title: "New Post"},
  {id:5, title: "Old Post"}
];
var comment = {id:1, postID:4,comment:"test1"};
function postComment(posts,comment){  
  return posts.find(function(post){
    return post.id === comment.postID
  });
}
console.log(postComment(posts,comment));
```
```
var users = [
  { id: 1, admin: false },
  { id: 2, admin: false },
  { id: 3, admin: true }
];

var admin = users.find(function(user){
    return user.admin === true
});

console.log(admin); // to fetch the admin values
```
```
var accounts = [
  { balance: -10 },
  { balance: 12 },
  { balance: 0 }
];

var account = accounts.find(function(account){
    return account.balance === 12;
});

console.log(account);
```
```
var ladders = [
  {height: '20 feet'},
  {height: '10 feet'},
  {height: '30 feet'}
  ];
function findWhere(array, criteria) {
    return array.find(function(ladder){
        return ladder.height ===  criteria.height
    })
}
console.log(findWhere(ladders, {height: '20 feet'}));
```
### Reduce ###

The reduce() method executes a reducer function (that you provide) on each element of the array, resulting in a `single output value`.

```
Syntax:

array.reduce(function(finalValue, arrayValue){
}, Initial Value)
```
```
const array1 = [1, 2, 3, 4];
const reducer = (accumulator, currentValue) => accumulator + currentValue;
--------  or  -------------
const reducer = function(accumulator,currentValue){
  return accumulator + currentValue;
}
// 1 + 2 + 3 + 4
console.log(array1.reduce(reducer));
// expected output: 10

// 5 + 1 + 2 + 3 + 4
console.log(array1.reduce(reducer, 5));
// expected output: 15

```
The reducer function takes four arguments:

  * Accumulator (acc)
  * Current Value (cur)
  * Current Index (idx)
  * Source Array (src)
  
Reducer function's returned value is assigned to the accumulator, whose value is remembered across each iteration throughout the array and ultimately becomes the final, single resulting value.

The first time the callback is called, accumulator and currentValue can be one of two values. If initialValue is provided in the call to reduce(), then accumulator will be equal to initialValue, and currentValue will be equal to the first value in the array. 

If no initialValue is provided, then accumulator will be equal to the first value in the array, and currentValue will be equal to the second.

```
var inputs = [10,20,30];
var test = inputs.reduce(function(sum,input){
  return sum + input
},0)
console.log(test); // 60
```
```
var colors = [
  {color: 'blue'},
  {color: 'Red'},
  {color: 'Green'}
];

var test = colors.reduce(function(accumlator,currentValue){
    accumlator.push(currentValue.color);
    return accumlator;
},[]);

console.log(test);
```
```
Check Balanced paranthesis => which will give opening and closing paranthesis () , (()), (((()))), )(
function balancedParans(string){
  return string.split("").reduce(function(previous,char){
      if(previous < 0){ return previous;}
      if(char === '(') return ++previous;
      if(char === ')') return --previous;
      return previous;
  },0)
}

balancedParans("(())");
```
```
var trips = [{ distance: 34 }, { distance: 12 } , { distance: 1 }];

var totalDistance = trips.reduce(function(acc,currentValue){
    return acc + currentValue.distance;
},0);

console.log(totalDistance);
```

```
var desks = [
  { type: 'sitting' },
  { type: 'standing' },
  { type: 'sitting' },
  { type: 'sitting' },
  { type: 'standing' }
];

var deskTypes = desks.reduce(function(acc, currentValue) {
    if(currentValue.type === 'sitting')  {
      acc.sitting++;
    }
    if(currentValue.type === 'standing')  {
      acc.standing++;
    }
    return acc;
}, { sitting: 0, standing: 0 });

console.log(deskTypes); // will return {'sitting': 3, 'standing':2}
```
```
var numbers = [1,1,2,3,4,4];

function unique(array) {
  return array.reduce(function(acc,number){
      if(!acc.includes(number)) {
          acc.push(number);
      }
      return acc;
  },[])
}

console.log(unique(numbers));
```
## Temaplte Strings / Literals ##
In ES5 we use single quote(') or double quote("") to concate string literals.
In ES6 we have a backticks(` `) to wrap the string literals.

  * let simple = `This is a template literal`;

following are the features of Template strings:

***Multiline string:*** a string that can span multiple lines.
***String formatting:*** the ability to substitute part of the string for the values of a variable or an expression. This feature is also called string interpolation.
***HTML escaping:*** the ability to transform a string so that it is safe to include in HTML.

Examples: 
```let str = `Template literal in ES6`;```
```
let msg = `Multiline \n\
string`;
console.log(msg);
//Multiline
//string
```
```
var {title, exceprt, body, tags} = post;
 
var postHtml = `<article>
<header>
    <h1>${title}</h1>
</header>
<section>
    <div>${exceprt}</div>
    <div>${body}</div>
</section>
<footer>
    <ul>
      ${tags.map(tag => `<li>${tag}</li>`).join('\n      ')}
    </ul>
</footer>`;
```
```
let firstName = 'John',
    lastName = 'Doe';
 
let greeting = `Hi ${firstName}, ${lastName}`;
console.log(greeting); // Hi John, Doe
```
Any valid javascript expression we can put inside the curly braces {}.

```
function doubleMessage(number) {
  return `Your number doubled is ${2 * number}`;
}
console.log(doubleMessage(2)); // 'Your number doubled is 4'
```
```
function fullName(firstName, lastName) {
  return `${firstName} ${lastName}`;
}

let firstName = "Alex";
let lastName = "Bob";
console.log(fullName(firstName,lastName));
```
## Arrow Functions ##

ES6 provides the arrow function with an alternative way to write a shorter syntax compared to the function expression. See the following example.
```
ES5:
var add = function(x,y) {
  return x + y;
}
console.log(add(10,20)); // 30
```
```
ES6:
var add = (x,y) => {
  return x + y;
}
console.log(add(10,20)); // 30
```
```
If the javascript returns `single JS expression` then no need of return statement.
Implicit return expression is, whatever the expression after the fatArrow will return automatically.
var add = (x,y) => x + y;
console.log(add(10,20)); // 30
```
```
const team = {
  members : ['Bill', 'Alex'],
  teamName: 'Super 30',
  teamSummary: function(){
    return this.members.map(function(member){
      // here this will throws us an error this is undefined to fetch teamName property
      // as this scope has been changed and it is trying to fetch from map iteration.
      // to avoid this we can bind the callback or cache the this scope into another variable
      return `${member} is in the team ${this.teamName}`
    })
  }
}
    1) Bind callback to current scope
    return this.members.map(function(member){
      // to avoid this we can bind the callback
      return `${member} is in the team ${this.teamName}`
    }.bind(this))
    
    2) By caching this into a variable
    return this.members.map(function(member){
      var self = this;
      // cache the this scope into another variable
      return `${member} is in the team ${self.teamName}`
    })
    
    3) By using Arrow functions will resolve the scope issues
    // fat arrow functions make use of Lexical this (scope).Here this means team
    return this.members.map( (member) => {
      return `${member} is in the team ${this.teamName}`
    })
```
```
const fibonacci = n => {
  if (n < 3) return 1;
  return fibonacci(n - 1) + fibonacci(n - 2);
};

fibonacci(8);
```
## Rest and Spread Operators ##
ES6 provides a new kind of parameter so-called rest parameter that has a prefix of three dots (...). 
The rest parameter allows you to represent an indefinite number of arguments as an array.
```
function sum(...args) {
    let total = 0;
    for (const a of args) {
        total += a;
    }
    return total;
}
 
sum(1, 2, 3); // 6
```

ES6 provides a new operator called spread operator that consists three dots (...). The spread operator allows you to spread out elements of an array or a string.

The spread operator allows you to insert another array into the initialized array when you construct an array using the literal form.

```
let initialChars = ['A', 'B'];
let chars = [...initialChars, 'C', 'D'];
console.log(chars); // ["A", "B", "C", "D"]
```

Also, you can use the spread operator to concatenate two or more arrays:
```
let numbers = [1, 2];
let moreNumbers = [3, 4];
let allNumbers = [...numbers, ...moreNumbers];
console.log(allNumbers); // [1, 2, 3, 4]
```

In addition, you can copy an array instance by using the spread operator.
```
let scores = [80, 70, 90];
let copiedScores = [...scores];
console.log(copiedScores); // [80, 70, 90]
```

```
function product(...numbers) {

  return numbers.reduce(function(acc, number) {
    return acc * number;
  }, 1)
}

console.log(product(1,2,3,4,5,6));
```
```
function unshift(numbers,...alpha) {
  return [...alpha,...numbers];
}
unshift([1,2],'a','b','r');
```
## Promises ##

A promise is a placeholder that represents the result of an `asynchronous operation`. ES6 supported the promises by providing the Promise object.
A promise has three states: 
    * pending (UnResolved)
    * fulfilled (Resolved)
    * Rejected

Each promise starts in the `pending` state which indicates that the asynchronous operation hasn’t completed. A pending promise is considered `unsettled`.

When the asynchronous operation completes, the promise is settled and has one of two possible states:

    * `Fulfilled` indicates that the asynchronous operation has completed successfully.
    * `Rejected` indicates that the error occurred that in asynchronous operation.

To create a promise, you use the `Promise constructor`. The Promise constructor accepts a function, which is called the `executor`.

The executor accepts two functions named `resolve()` and `reject()`. You call the resolve() function when the executor completed successfully and call the reject() function when the executor failed.


```
let p = new Promise( function(resolve,reject){
});
p.then();
p.catch();
```

```
let promise = new Promise( function(resolve,reject){
  resolve();
});

promise
    .then(function(){
      console.log("resoved successfully");
     })
     .then(function(){
      console.log("resoved successfully");
     })
     .catch(function(){
      console.log("rejected error");
     });

```
Consuming functions can be registered (subscribed) using methods .then, .catch and .finally.

```
let promise = new Promise(function(resolve, reject) {
  setTimeout(() => resolve("done!"), 1000);
});

// resolve runs the first function in .then
promise.then(
  result => alert(result), // shows "done!" after 1 second
  error => alert(error) // doesn't run
);
```
Fetch is a helper.fetch() is available in the latest version of Chrome, Firefox, and Opera, but not in IE and Safari. 

```
fetch("https://jsonplaceholder.typicode.com/posts")
.then(response => response.json())
.then(data => console.log(data))
```
returns an error status code so any status could above 300 It does not enter the catch case.
It will catch the error when the network fails.Fetch only hits catch when the network request flat out fails to be issued at all if the request hits.

## Examples ##
```
//fibnocci series

function fibonacci(n){
  var a = 0, b = 1;
  
  for (i=0; i< n; i++){
    console.log(a);
    c = a + b;
    a = b;
    b = c;
  }
}

fibonacci(8);
```
```
let obj = {
    name: 'Krunal',
    education: 'IT Engineer'
} ;
console.log(Object.keys(obj)); // (2) ["name" ,"education"]
console.log(Object.values(obj));(2) ["Krunal" ,"IT Engineer"]
```
