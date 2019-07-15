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
