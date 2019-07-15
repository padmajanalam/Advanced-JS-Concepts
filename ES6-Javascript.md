# ES6 - Javascript Concepts

## Array Helper Methods ##

* ForEach
* Map
* Filter
* Find
* Every
* Some
* Reduce

#### Foreach ####

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

## Examples ##

```
let obj = {
    name: 'Krunal',
    education: 'IT Engineer'
} ;
console.log(Object.keys(obj)); // (2) ["name" ,"education"]
console.log(Object.values(obj));(2) ["Krunal" ,"IT Engineer"]
```
