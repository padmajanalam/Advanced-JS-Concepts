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
