# How to Clone an array in javascript

## Spread Operator (Shallow copy)
 - The `spread operator` is a new addition to the features available in the JavaScript `ES6 `version.
 - The spread operator ... is used to `expand` or `spread` an `iterable` or an `array`.

*example*
```js
numbers = [1, 2, 3];
numbersCopy = [...numbers];
```

```js
numbersCopy.push(4);
console.log(numbers, numbersCopy);
// [1, 2, 3] and [1, 2, 3, 4]
// numbers is left alone
```

```js
nestedNumbers = [[1], [2]];
numbersCopy = [...nestedNumbers];

numbersCopy[0].push(300);
console.log(nestedNumbers, numbersCopy);
// [[1, 300], [2]]
// [[1, 300], [2]]
// They've both been changed because they share references
```
> **Note :** This doesn’t safely copy multi-dimensional arrays. Array/object values are copied by reference instead of by value.

## for loop 

*example*

```js
numbers = [1, 2, 3];
numbersCopy = [];

for (i = 0; i < numbers.length; i++) {
  numbersCopy[i] = numbers[i];
}

numbersCopy.push(4);
console.log(numbers, numbersCopy);
// [1, 2, 3] and [1, 2, 3, 4]
// numbers is left alone

```

## map

- The map() method in JavaScript creates an array by calling a specific function on each element present in the parent array. It is a non-mutating method. 
- Generally map() method is used to iterate over an array and calling function on every element of array.
  
*syntax*
```js
array.map(function(currentValue, index, arr), thisValue)
```
*example*

```js
numbers = [1, 2, 3];
double = (x) => x * 2;

numbers.map(double);


numbers = [1, 2, 3];
numbersCopy = numbers.map((x) => x);


identity = (x) => x;
numbers.map(identity);
// [1, 2, 3]
```

## Array.filter (Shallow copy)

- This function returns an array, just like map, but it’s not guaranteed to be the same length.
  
*example*
```js
// What if you’re filtering for even numbers?
[1, 2, 3].filter((x) => x % 2 === 0);
// [2]
```
- The input array length was 3, but the resulting length is 1.

- If your filter's predicate always returns true, however, you get a duplicate!
```js
numbers = [1, 2, 3];
numbersCopy = numbers.filter(() => true);
```
- Every element passes the test, so it gets returned.

> **Note :** This also assigns objects/arrays by reference instead of by value.

## Array.reduce (Shallow copy)
- I almost feel bad using reduce to clone an array, because it’s so much more powerful than that. But here we go…

*example*

```js
numbers = [1, 2, 3];

numbersCopy = numbers.reduce((newArray, element) => {
  newArray.push(element);

  return newArray;
}, []);
```


## Array.slice (Shallow copy)

- slice returns a shallow copy of an array based on the provided start/end index you provide.

*example*

```js
//If we want the first 3 elements:

[1, 2, 3, 4, 5].slice(0, 3);
// [1, 2, 3]
// Starts at index 0, stops at index 3
If we want all the elements, don’t give any parameters

numbers = [1, 2, 3, 4, 5];
numbersCopy = numbers.slice();
// [1, 2, 3, 4, 5]
```

> **Note :** This is a shallow copy, so it also assigns objects/arrays by reference instead of by value.

## JSON.parse and JSON.stringify (Deep copy)
- JSON.stringify turns an object into a string.

- JSON.parse turns a string into an object.

- Combining them can turn an object into a string, and then reverse the process to create a brand new data structure.


*example*

```js
nestedNumbers = [[1], [2]];
numbersCopy = JSON.parse(JSON.stringify(nestedNumbers));

numbersCopy[0].push(300);
console.log(nestedNumbers, numbersCopy);

// [[1], [2]]
// [[1, 300], [2]]
// These two arrays are completely separate!
```
>**Note :** This one safely copies deeply nested objects/arrays!

## Array.concat (Shallow copy)

- concat combines arrays with values or other arrays.
  
*example*

```js
[1, 2, 3].concat(4); // [1, 2, 3, 4]
[1, 2, 3].concat([4, 5]); // [1, 2, 3, 4, 5]
```
- If you give nothing or an empty array, a shallow copy’s returned.

```js
[1, 2, 3].concat(); // [1, 2, 3]
[1, 2, 3].concat([]); // [1, 2, 3]
```

>**Note :** This also assigns objects/arrays by reference instead of by value.

## Array.from (Shallow copy)
- This can turn any iterable object into an array. Giving an array returns a shallow copy.

*example*
  
```js
numbers = [1, 2, 3];
numbersCopy = Array.from(numbers);
// [1, 2, 3]
```
> **Note :** This also assigns objects/arrays by reference instead of by value.