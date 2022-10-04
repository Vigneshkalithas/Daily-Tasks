# Array methods

## toString()

- The JavaScript method toString() converts an array to a string of (comma separated) array values.

*example 1*
```js 
var array = ["vignesh", "kalithas", "dinesh"];
console.log(array.toString());
// vignesh,kalithas,dinesh
```
*example 2*
```js 
var array = [1,"vignesh", 8 , null ,9,undefined,true,20 , 0 ,NaN , false , "kalithas", {},["u", 1,"gh"], 'dinesh']
console.log(array.toString())

1,vignesh,8,,9,,true,20,0,NaN,false,kalithas,[object Object],u,1,gh,dinesh
```
- they converted nested array also String. 

- doubt - why to string skip null and undefined 



## array.join()

- The join() method creates and returns a new string by concatenating all of the elements in an array
- (or an array-like object), separated by commas or a specified separator string.
If the array has only one item, then that item will be returned without using the separator. 

*syntax* 
```js
join()
join(separator)
```
```js
var array = ["vignesh", "kalithas", "dinesh" ,1 , null ,5, undefined];

console.log(array.join());
// expected output: "vignesh,kalithas,dinesh,1,,5,"

console.log(array.join(''));
// expected output: "vigneshkalithasdinesh15"

console.log(array.join('-'));
// expected output: "vignesh-kalithas-dinesh-1--5-""
```


- The string conversions of all array elements are joined into one string.
- If an element is undefined, null, 
-  it is converted to an empty string instead of the string "null" or "undefined".



## array.lenght
- This is method is use to find the length of the array.
```js
var array  = [1, "vignesh", null, true , undefined]
console.log(`array.length is ${array.length}`);

```
## array.pop()

- The pop() method removes the last element from an array:
```js
var array = ["vignesh", "kalithas", "dinesh"];
var result = array.pop();
console.log(array);
```
- last element 'dinesh' was removed in the array

## array.push()
- The push() method adds a new element to an array (at the end).
  
```js
var array = ["vignesh" , 4];
array.push("kalithas");
console.log(array);
```



## array.shift
- The shift() method removes the first element from an array and returns that removed element. 
- This method changes the length of the array.

```js
const fruits = ["vignesh", "kalithas", "dinesh", "karthi"];
fruits.shift();
console.log(fruits);
```

## array.unshift()

- The unshift() method adds one or more elements to the beginning of an array and returns the new length of the array.
```js
var array = ["kalithas" , "dinesh" , "karthi"];
array.unshift("vignesh");
console.log(array);

```

## delete() operator

- Array elements can be deleted using the JavaScript operator delete.

- Using delete leaves undefined holes in the array.

- Use pop() or shift() instead.

```js
const Employee = {
   firstname: 'John',
   lastname: 'Doe'
 };
 
 console.log(Employee.firstname);
 // expected output: "John"
 
 delete Employee.firstname;
 
 console.log(Employee.firstname);
 // expected output: undefined

 var array = ["vignesh" ,2,"kalithas"]

delete array[0];
console.log(array)
//[empty, 2, null, undefined, 'kalithas']
```
- Using delete leaves undefined holes in the array.

## array.concat()

- The concat() method is used to merge two or more arrays.
- This method does not change the existing arrays,
- but instead returns a new array.

*Syntax*
```js
concat()
concat(value0)
concat(value0, value1)
concat(value0, value1, /* … ,*/ valueN)
```

```js
var array1 = ['a', 'b', 'c'];
var array2 = ['d', 'e', 'f'];
var array3 = array1.concat(array2);

console.log(array3);
// expected output: Array ["a", "b", "c", "d", "e", "f"]

// Concatenating two arrays

var letters = ["a", "b", "c"];
var numbers = [1, 2, 3];

var alphaNumeric = letters.concat(numbers);
console.log(alphaNumeric);
// results in ['a', 'b', 'c', 1, 2, 3]


// Concatenating three arrays
// The following code concatenates three arrays:

var num1 = [1, 2, 3];
var num2 = [4, 5, 6];
var num3 = [7, 8, 9];

var numbers = num1.concat(num2, num3);

console.log(numbers);
// results in [1, 2, 3, 4, 5, 6, 7, 8, 

// Concatenating values to an array
// The following code concatenates three values to an array:

var letters = ["a", "b", "c"];

var alphaNumeric = letters.concat(1, [2, 3]);

console.log(alphaNumeric);
// results in ['a', 'b', 'c', 1, 2, 3]

// Concatenating nested arrays
// The following code concatenates nested arrays and demonstrates retention of references:

var num1 = [[1]];
var num2 = [2, [3]];
var numbers = num1.concat(num2);

console.log(numbers);
// results in [[1], 2, [3]]

// modify the first element of num1
num1[0].push(4);

console.log(numbers);
// results in [[1, 4], 2, [3]]


// Using concat() on sparse arrays
// If any of the source arrays is sparse, the resulting array will also be sparse:

console.log([1, , 3].concat([4, 5])); // [1, empty, 3, 4, 5]
console.log([1, 2].concat([3, , 5])); // [1, 2, 3, empty, 6]
```

## array.splice()  

- The splice() method changes the contents of an array by removing or replacing existing elements and/or addingnew elements in place

*Syntax*
```js
splice(start)
splice(start, deleteCount)
splice(start, deleteCount, item1)
splice(start, deleteCount, item1, item2, itemN)
```

### start

- The index at which to start changing the array.

- If greater than the length of the array, start will be set to the length of the array. In this case, no element will be deleted but the method will behave as an adding function, adding as many elements as items provided.

- If negative, it will begin that many elements from the end of the array. (In this case, the origin -1, meaning -n is the index of the nth last element, and is therefore equivalent to the index of array.length - n.) If start is -Infinity, it will begin from index 0.

### deleteCount Optional

- An integer indicating the number of elements in the array to remove from start.

- If deleteCount is omitted, or if its value is equal to or larger than array.length - start (that is, if it is equal to or greater than the number of elements left in the array, starting at start), then all the elements from start to the end of the array will be deleted. However, it must not be omitted if there is any item1 parameter.

- If deleteCount is 0 or negative, no elements are removed. In this case, you should specify at least one new element (see below).

### item1, …, itemN Optional

- The elements to add to the array, beginning from start.

- If you do not specify any elements, splice() will only remove elements from the array.

*Examples*

- Remove 0 (zero) elements before index 2, and insert "drum"

```js
var myFish = ['angel', 'clown', 'mandarin', 'sturgeon'];
var removed = myFish.splice(2, 0, 'drum');
console.log(`myFish : ${myFish} , removed : ${removed}`)

// myFish is ["angel", "clown", "drum", "mandarin", "sturgeon"]
// removed is [], no elements removed

// Remove 0 (zero) elements before index 2, and insert "drum" and "guitar"

var myFish = ['angel', 'clown', 'mandarin', 'sturgeon'];
var removed = myFish.splice(2, 0, 'drum', 'guitar');
console.log(`myFish : ${myFish} , removed : ${removed}`)


// myFish is ["angel", "clown", "drum", "guitar", "mandarin", "sturgeon"]
// removed is [], no elements removed

// Remove 1 element at index 3

var myFish = ['angel', 'clown', 'drum', 'mandarin', 'sturgeon'];
var removed = myFish.splice(3, 1);
console.log(`myFish : ${myFish} , removed : ${removed}`)


// myFish is ["angel", "clown", "drum", "sturgeon"]
// removed is ["mandarin"]

// Remove 1 element at index 2, and insert "trumpet"

var myFish = ['angel', 'clown', 'drum', 'sturgeon'];
var removed = myFish.splice(2, 1, 'trumpet');
console.log(`myFish : ${myFish} , removed : ${removed}`)


// myFish is ["angel", "clown", "trumpet", "sturgeon"]
// removed is ["drum"]

// Remove 2 elements from index 0, and insert "parrot", "anemone" and "blue"

var myFish = ['angel', 'clown', 'trumpet', 'sturgeon'];
var removed = myFish.splice(0, 2, 'parrot', 'anemone', 'blue');
console.log(`myFish : ${myFish} , removed : ${removed}`)


// myFish is ["parrot", "anemone", "blue", "trumpet", "sturgeon"]
// removed is ["angel", "clown"]

// Remove 2 elements, starting from index 2

var myFish = ['parrot', 'anemone', 'blue', 'trumpet', 'sturgeon'];
var removed = myFish.splice(2, 2);
console.log(`myFish : ${myFish} , removed : ${removed}`)


// myFish is ["parrot", "anemone", "sturgeon"]
// removed is ["blue", "trumpet"]

// Remove 1 element from index -2

var myFish = ['angel', 'clown', 'mandarin', 'sturgeon'];
var removed = myFish.splice(-2, 1);
console.log(`myFish : ${myFish} , removed : ${removed}`)


// myFish is ["angel", "clown", "sturgeon"]
// removed is ["mandarin"]

// Remove all elements, starting from index 2

var myFish = ['angel', 'clown', 'mandarin', 'sturgeon'];
var removed = myFish.splice(2);
console.log(`myFish : ${myFish} , removed : ${removed}`)


// myFish is ["angel", "clown"]
// removed is ["mandarin", "sturgeon"]

// Using splice() on sparse arrays
// The splice() method preserves the array's sparseness.

var arr = [1, , 3, 4, , 6];
console.log(arr.splice(1, 2)); // [empty, 3]
console.log(arr); // [1, 4, empty, 6]

```


## slice
 
- The slice() method returns a shallow copy of a portion of an array into a 
- new array object selected from start to end (end not included) where start and end represent the index of items in that array.
- The original array will not be modified.

*syntax*
```js
slice()
slice(start)
slice(start, end)
```

### Parameters
#### *start Optional*
>- Zero-based index at which to start extraction.
>
>- A negative index can be used, indicating an offset from the end of the sequence. slice(-2) extracts the last two elements in the sequence.

>- If start is undefined, slice starts from the index 0.

>- If start is greater than the index range of the sequence, an empty array is returned.

#### *end Optional*

>- The index of the first element to exclude from the returned array. slice extracts up to but not including end. For example, slice(1,4) extracts the second element through the fourth element (elements indexed 1, 2, and 3).
>
>- A negative index can be used, indicating an offset from the end of the sequence. slice(2,-1) extracts the third element through the second-to-last element in the sequence.
>
>- If end is omitted, slice extracts through the end of the sequence (arr.length).
>
>- If end is greater than the length of the sequence, slice extracts through to the end of the sequence (arr.length).

#### *Return value*

>- A new array containing the extracted elements.

#### *Description*
- The slice() method is a copying method. It does not alter this but instead returns a shallow copy that contains some of the same elements as the ones from the original array.

- The slice() method preserves empty slots. If the sliced portion is sparse, the returned array is sparse as well.

```js

var animals = ['ant', 'bison', 'camel', 'duck', 'elephant'];

console.log(animals.slice(2));
// expected output: Array ["camel", "duck", "elephant"]

console.log(animals.slice(2, 4));
// expected output: Array ["camel", "duck"]

console.log(animals.slice(1, 5));
// expected output: Array ["bison", "camel", "duck", "elephant"]

console.log(animals.slice(-2));
// expected output: Array ["duck", "elephant"]

console.log(animals.slice(2, -1));
// expected output: Array ["camel", "duck"]

console.log(animals.slice());
// expected output: Array ["ant", "bison", "camel", "duck", "elephant"]
```

### array.reverse()

- The reverse() method returns the array in reverse order.

*syntax* 
```js
arr.reverse()
```

- The reverse() method does not take any parameters.
```js

var numbers = [1, 2, 3, 4, 5];

var reversedArray = numbers.reverse();

console.log(reversedArray);

// Output: [ 5, 4, 3, 2, 1 ]

console.log(numbers);

// Reversed Array: [  5, 4, 3, 2, 1 ]
// Original Array: [ 5, 4, 3, 2, 1 ]

//its sffect the original array

// The reverse() method reverses the order of elements in place, it means the method changes the original array.


// reverse() Method with Spread Operator


var languages = ["JavaScript", "Python", "C++", "Java", "Lua"];

// using spread operator to reverse the array
var reversedArray = [...languages].reverse();

console.log("Reversed Array:", reversedArray);

// modifies the original array
console.log("Original Array:", languages);

```

- Reversed Array: [ 'Lua', 'Java', 'C++', 'Python', 'JavaScript' ]

- Original Array: [ 'JavaScript', 'Python', 'C++', 'Java', 'Lua' ] 

*`spread` operator just only spread the vale (copy by value)*


## array.sort()

- The sort() method sorts the items of an array in a specific order (ascending or descending).
 
- Returns the array after sorting the elements of the array in place (meaning that it `changes the original` array and no copy is made).

*syntax*

```js
arr.sort(compareFunction)
```

- compareFunction (optional) - It is used to define a custom sort order.

```js
// sorting an array of strings
var names = ["Adam", "Jeffrey", "Fabiano", "Danil", "Ben"];

// returns the sorted array
console.log(names.sort());

// modifies the array in place
console.log(names);

var priceList = [1000, 50, 2, 7, 14];
priceList.sort();

// Number is converted to string and sorted
console.log(priceList)

```
*output*
```js
[ 'Adam', 'Ben', 'Danil', 'Fabiano', 'Jeffrey' ]
[ 'Adam', 'Ben', 'Danil', 'Fabiano', 'Jeffrey' ]
[ 1000, 14, 2, 50, 7 ]
```

- Here, we can see that even though 1000 is greater than 50 numerically, it comes at the beginning of the sorted list. It is because "1" < "5".


# array.fill()

- The fill() method returns an array by filling all elements with a specified value.

*syntax*

```js
arr.fill(value, start, end)
```

```js
// defining an array 
var fruits = ['Apple', 'Banana', 'Grape'];

// filling every element of the array with 'Cherry'
fruits.fill("Cherry");

console.log(fruits);

// Output: 
// [ 'Cherry', 'Cherry', 'Cherry' ]
```

#### fill() Parameters
> *The fill() method can take 3 parameters:*>
>- value - Value to fill the array with.
>- start (optional) - Start index (default is 0).
>- end (optional) - End index (default is Array.length), which is always excluded.

#### fill() Return Value
> *Returns the modified array, filled with value from start to end.*
>
>- If start or end is negative, indexes are counted backwards.
>- Since fill() is a mutator method, `it changes the array itself (not a copy) and returns it`.


```js
var prices = [651, 41, 4, 3, 6];

// filling every element of the array with '5'
new_prices = prices.fill(5);

console.log(prices);

console.log(new_prices); 


[ 5, 5, 5, 5, 5 ]
[ 5, 5, 5, 5, 5 ]

```


####  fill() Method with Three Arguments

```js
var language = ["swift", "Python", "C", "C++"];

// replacing element of array from index 1 to 3 by 'JavaScript'
language.fill("JavaScript", 1, 3);

// printing the original array
console.log(language);

var language = ["grandpa", "grandma", "dad", "mom", "brother"];

// replacing element of array from index 1 to 3 by 'JavaScript'
language.fill("son", 1, 5);

// printing the original array
console.log(language);

```


#### fill() Method with Invalid Indexes
```js
var rank = [8, 9, 3, 7];

// on passing negative index, counting starts from back
rank.fill(15, -2);

// prints the modified 'rank' array
console.log(rank);  // [ 8, 9, 15, 15 ]

// passing invalid index result in no change
rank.fill(15, 7, 8);

console.log(rank);  // [ 8, 9, 15, 15 ]

// passing invalid indexes
rank.fill(15, NaN, NaN);

console.log(rank);  // [ 8, 9, 15, 15 ]

```

# array.lastIndexOf()
- The lastIndexOf() method returns the index of the last occurrence of a specified element in the array.

*syntax*
```js
arr.lastIndexOf(searchElement, fromIndex)
```

```js
let priceList = [10, 8, 2, 31, 10, 31, 65];

// finding the index of the last occurence of 31
let lastIndex = priceList.lastIndexOf(31);

console.log(lastIndex); 

// Output: 5
```

#### Parameters

>- *searchElement* - The element to locate in the array.
>- *fromIndex (optional)* - The index to start searching backwards. By default it is array.length - 1.


#### Return Value

>- the last index of the element in the array if it is present at least once.
>- -1 if the element is not found in the array.

```js
let alphabets = ["a", "b", "c", "a", "d"];

// finding the index of the last occurence of 'a'
let lastIndex1 = alphabets.lastIndexOf("a");

console.log(lastIndex1);
// output : 3

// finding the index of the last occurence of 'e'
let lastIndex2 = alphabets.lastIndexOf("e");

console.log(lastIndex2);
// output : -1
```


#### two Parameters

```js

let alphabets = ["a", "b", "c", "a", "d", "a"];

// second argument specifies the starting index
// from where the method searches the element backward
let lastIndex = alphabets.lastIndexOf("a", 4);

console.log(lastIndex); 
// output : 3 
```




#### Negative Parameter
```js

let alphabets = ["a", "b", "c", "a", "d"];

// starts the search at third last position
let lastIndex = alphabets.lastIndexOf("a", -3);

console.log(lastIndex);

// output : 0 
```

# array.indexOf()


- The indexOf() method returns the first index of occurance of an array element, or -1 if it is not found.

*Examples*
```js
let languages = ["Java", "JavaScript", "Python", "JavaScript"];

// get the index of the first occurrence of "JavaScript"
let index = languages.indexOf("JavaScript");
console.log(index);

// Output: 1
```
*Syntax*
```js
arr.indexOf(searchElement, fromIndex)
```
#### Parameters

- searchElement - The element to locate in the array.
- fromIndex (optional) - The index to start the search at. By default, it is 0.

#### Return Value
- Returns the first index of the element in the array if it is present at least once.
- Returns -1 if the element is not found in the array.
> - *Note* : indexOf() compares searchElement to elements of the Array using strict equality (similar to triple-equals operator or ===).

```js
var priceList = [10, 8, 2, 31, 10, 1, 65];

// indexOf() returns the first occurance
var index1 = priceList.indexOf(31);
console.log(index1); // 3

var index2 = priceList.indexOf(10);
console.log(index2); // 0

// second argument specifies the search's start index
var index3 = priceList.indexOf(10, 1);
console.log(index3); // 4

// indexOf returns -1 if not found
var index4 = priceList.indexOf(69.5);
console.log(index4); // -1

```

# Array constructor

- The constructor property returns the constructor function for the array.

*syntax*
```js
arr.constructor
```
```js
let languages = ["JavaScript", "Java", "Python"];

let constructor = languages.constructor;
console.log(constructor)

// Output:
// [Function: Array]
```

#  Array copyWithin()
- The copyWithin() method copies array elements from one position to another in the given array.

*syntax*
>- arr.copyWithin(target, start, end)

```js
let words = ["apple", "ball", "cat", "dog"];

// copies element from index 0 to index 3 
words.copyWithin(3, 0);

// modifies the original array 
console.log(words);

// Output: 
// [ ''apple'', ''ball'', ''cat'', ''apple'' ]
```

#### Parameters

- target - The index position to copy the elements to.
- start (optional) - The index position to start copying elements from. If omitted, it will copy from index 0.
- end (optional) - The index position to stop copying elements from (end element not included). If omitted, it will copy until the last index.

#### Return Value
- Returns the `modified array` after copying the elements.
- overwrites the original array.
- does not change the length of the original array.

```js
let numbers = [1, 2, 3, 4, 5];

// copying element located at 4th index to 0th index
numbers.copyWithin(0, 4);

// modifies the original array
console.log(numbers); // [ 5, 6, 3, 4, 5 ]

let letters = ["a", "b", "c", "d"];

// copying element located at 1st index to 2nd index
letters.copyWithin(2, 1);

// modifies the original array 
console.log(letters); // [ 'a', 'b', 'b', 'c' ]
```


```js
let laptops = ["dell", "hp", "acer", "asus"];

// copying elements from index 2 to 4(excluding 4) to index 0
laptops.copyWithin(0, 2, 4);

// modifies the original array
console.log(laptops); // [ 'acer', 'asus', 'acer', 'asus' ]
```

```js
let evenNumbers= [2,4,6,8];

// passing negative index value -1 as target index 
evenNumbers.copyWithin(-1);

console.log(evenNumbers);
```



# Array entries()

- The entries() method returns a new Array Iterator object containing key/value pairs for each array index.

*Syntax*
```js
arr.entries()
```

Example


```js
// defining an array named alphabets
const alphabets = ["A", "B", "C"];

// array iterator object that contains
// key-value pairs for each index in the array
let iterator = alphabets.entries();

// iterating through key-value pairs in the array
for (let entry of iterator) {
  console.log(entry);
}

// Output: 
// [ 0, 'A' ]
// [ 1, 'B' ]
// [ 2, 'C' ]
```
```js
// defining an array 
const languages = ["Java", "C", "C++", "Python"];

// array iterator object that contains
// key-value pairs for each index in the array
let iterator = languages.entries();

// looping through key-value pairs in the array
for (let entry of iterator) {
  console.log(entry);
}

[ 0, 'Java' ]
[ 1, 'C' ]
[ 2, 'C++' ]
[ 3, 'Python' ]

```

# array.every()

-The JavaScript Array every() method checks if all the array elements pass the given test function.

*syntax*
```js
arr.every(callback(currentValue), thisArg)
```

```js
function checkAdult(age) {
    return age >= 18;
}

const ageArray = [34, 23, 20, 26, 12];
let check = ageArray.every(checkAdult); // false

if (!check) {
    console.log("All members must be at least 18 years of age.")
}

// using arrow function
let check1 = ageArray.every(age => age >= 18); // false
console.log(check1);

// output : All members must be at least 18 years of age.
false
```

```js
[3,4,5,6].every((num)=>num > 5) // false
[3,4,5,6].every((num)=>num > 2) // true
```


# array.some()

- The some() method tests whether any of the array elements pass the given test function.

*syntax*
```js
arr.some(callback(currentValue), thisArg)
```

```js
// a test function: returns an even number
function isEven(element) {
  return element % 2 === 0;
}

// defining an array
let numbers = [1, 3, 2, 5, 4];

// checks whether the numbers array contain at least one even number
console.log(numbers.some(isEven));

// Output: true 
```

```js
[3,4,5,6].some((num)=> num > 5); // true
[3,4,5,6].some((num)=> num > 7); // false
```


# array.filter()

- The filter() method returns a new array with all elements that pass the test defined by the given function.

```js
let numbers = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10];

// function to check even numbers
function checkEven(number) {
  if (number % 2 == 0)
    return true;
  else
    return false;
}

// create a new array by filter even numbers from the numbers array
let evenNumbers = numbers.filter(checkEven);
console.log(evenNumbers);

// Output: [ 2, 4, 6, 8, 10 ]
```

*Syntax*
```js
arr.filter(callback(element), thisArg)
```
#### Parameters

- callback - The test function to execute on each array element; returns true if element passes the test, else false. It takes in:

- element - The current element being passed from the array.

- thisArg (optional) - The value to use as this when executing callback. By default, it is undefined.
filter() Return Value

- Returns a new array with only the elements that passed the test.

- Filtering out values from Array
```js
const prices = [1800, 2000, null, 3000, 5000, "Thousand", 500, 8000]

function checkPrice(element) {
  return element > 2000 && !Number.isNaN(element);
}

let filteredPrices = prices.filter(checkPrice);
console.log(filteredPrices); // [ 3000, 5000, 8000 ]

// using arrow function
let newPrices = prices.filter((price) => (price > 2000 && !Number.isNaN(price)));
console.log(newPrices); // [ 3000, 5000, 8000 ]

// Output

[ 3000, 5000, 8000 ]
[ 3000, 5000, 8000 ]
```
Searching in Array
```js
const languages = ["JavaScript", "Python", "Ruby", "C", "C++", "Swift", "PHP", "Java"];

function searchFor(arr, query) {
    function condition(element) {
        return element.toLowerCase().indexOf(query.toLowerCase()) !== -1;
    }
    return arr.filter(condition);
}

let newArr = searchFor(languages, "ja");
console.log(newArr); // [ 'JavaScript', 'Java' ]

// using arrow function
const searchArr = (arr, query) => arr.filter(element => element.toLowerCase().indexOf(query.toLowerCase()) !== -1);

let newLanguages = searchArr(languages, "p");
console.log(newLanguages); // [ 'JavaScript', 'Python', 'PHP' ]
// Output

[ 'JavaScript', 'Java' ]
[ 'JavaScript', 'Python', 'PHP' ]
```

# array.find()
- The find() method returns the value of the first array element that satisfies the provided test function.

```js

let numbers = [1, 3, 4, 9, 8];

// function to check even number
function isEven(element) {
  return element % 2 == 0;
}

// get the first even number
let evenNumber = numbers.find(isEven);
console.log(evenNumber);

// Output: 4
```


```js
[3,4,5,6].find((num)=. num > 4) // 5
```


# array.findIndex()

- The findIndex() method returns the index of the first array element that satisfies the provided test function or else returns -1.
  
*Syntax*
```js 
arr.findIndex(callback(element, index, arr),thisArg)
```
```js
// function that returns odd number
function isOdd(element) {
  return element % 2 !== 0;
}

// defining an array of integers
let numbers = [2, 8, 1, 3, 4];

// returns the index of the first odd number in the array
let firstOdd = numbers.findIndex(isOdd);

console.log(firstOdd);

// Output: 2
```

```js
var array = [3,4,5,6]
var res = array.findIndex((num)=> num > 4 );
console.log(res)

```


#### Return Value
- Returns the index of the first element in the array that satisfies the given function.
- Returns -1 if none of the elements satisfy the function.

```js 
// function that returns even number
function isEven(element) {
  return element % 2 == 0;
}

// defining an array of integers
let numbers = [1, 45, 8, 98, 7];

// returns the index of the first even number in the array
let firstEven = numbers.findIndex(isEven);

console.log(firstEven); // 2

//Output

2
```
- The method returns 2 which is the index of the first even number in numbers i.e. 8.