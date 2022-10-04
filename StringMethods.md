# String methods

## JavaScript String Length

- The length property returns the length of a string:
```js
let txt = "ABCDEFGHIJKLMNOPQRSTUVWXYZ";
let length = txt.length; //26 
```

## JavaScript String slice()
- slice() extracts a part of a string and returns the extracted part in a new string.

- The method takes 2 parameters: the start position, and the end position (end not included).

- Slice out a portion of a string from position 7 to position 13 (13 not included):

```js
let str = "Apple, Banana, Kiwi";
let part = str.slice(7, 13);
 // "Banana"
```

- If a parameter is negative, the position is counted from the end of the string.

- This example slices out a portion of a string from position -12 to position -6:
- 
```js
let str = "Apple, Banana, Kiwi";
let part = str.slice(-12, -6);
"Banana"
```
- If you omit the second parameter, the method will slice out the rest of the string:
```js
let part = str.slice(7);
```
- or, counting from the end:
```
```js
let part = str.slice(-12);
```

## JavaScript String substring()

- The difference is that start and end values less than 0 are treated as 0 in substring().

```js
let str = "Apple, Banana, Kiwi";
let part = str.substring(7, 13);
// " Banana"
```

- If you omit the second parameter, substring() will slice out the rest of the string.


## JavaScript String substr()

- substr() is similar to slice().

- The difference is that the second parameter specifies the length of the extracted part.

```js
let str = "Apple, Banana, Kiwi";
let part = str.substr(7, 6);
//"Banana"
```

If you omit the second parameter, substr() will slice out the rest of the string.

```js
let str = "Apple, Banana, Kiwi";
let part = str.substr(7);
//"Banana" , "kiwi"
```

If the first parameter is negative, the position counts from the end of the string.

```js
let str = "Apple, Banana, Kiwi";
let part = str.substr(-4);
// "kiwi"
```

## Replacing String Content
- The replace() method replaces a specified value with another value in a string:
```js
let text = "Please visit Microsoft!";
let newText = text.replace("Microsoft", "W3Schools");
// Please visit W3Schools!
```

- The replace() method does not change the string it is called on.

- The replace() method returns a new string.

- The replace() method replaces only the first match

- If you want to replace all matches, use a regular expression with the /g flag set. See examples below.

- By default, the replace() method replaces only the first match:
- 
```js
let text = "Please visit Microsoft and Microsoft!";
let newText = text.replace("Microsoft", "W3Schools");
// Please visit Microsoft and Microsoft!
```
- By default, the replace() method is case sensitive. Writing MICROSOFT (with upper-case) will not work:

```js
let text = "Please visit Microsoft!";
let newText = text.replace("MICROSOFT", "W3Schools");
//The replace() method is case sensitive. MICROSOFT (with upper-case) will not be replaced.

```
- To replace case insensitive, use a regular expression with an /i flag (insensitive):

```js
let text = "Please visit Microsoft!";
let newText = text.replace(/MICROSOFT/i, "W3Schools");
// Please visit Microsoft!
```
- Regular expressions are written without quotes.

- To replace all matches, use a regular expression with a /g flag (global match):

```js
let text = "Please visit Microsoft and Microsoft!";
let newText = text.replace(/Microsoft/g, "W3Schools");
//Please visit Microsoft and Microsoft!

```
- You will learn a lot more about regular expressions in the chapter JavaScript Regular Expressions.


## JavaScript String toUpperCase()
- A string is converted to upper case with toUpperCase():

```js
let text1 = "Hello World!";
let text2 = text1.toUpperCase();
// HELLO WORLD!
```

## JavaScript String toLowerCase()

- A string is converted to lower case with toLowerCase():
```js
let text1 = "Hello World!";       // String
let text2 = text1.toLowerCase();  //hello world!
```

## JavaScript String concat()
concat() joins two or more strings:

```js
let text1 = "Hello";
let text2 = "World";
let text3 = text1.concat(" ", text2);
// Hello World!
```
- The concat() method can be used instead of the plus operator. These two lines do the same:
```js
text = "Hello" + " " + "World!";
text = "Hello".concat(" ", "World!");
// Hello World!
```
- All string methods return a new string. They don't modify the original string.
-Strings are immutable: Strings cannot be changed, only replaced.

## JavaScript String trim()
- The trim() method removes whitespace from both sides of a string:

```js
let text1 = "      Hello World!      ";
let text2 = text1.trim();
// "Hello World!"
```

## JavaScript String trimStart()
- ECMAScript 2019 added the String method trimStart() to JavaScript.

- The trimStart() method works like trim(), but removes whitespace only from the start of a string.

```js
let text1 = "     Hello World!     ";
let text2 = text1.trimStart();
// "Hello World!      "
```

## JavaScript String trimEnd()
- ECMAScript 2019 added the String method trimEnd() to JavaScript.

- The trimEnd() method works like trim(), but removes whitespace only from the end of a string.

```js
let text1 = "     Hello World!     ";
let text2 = text1.trimEnd();
// "      Hello World!"
```


## JavaScript String padStart()
- The padStart() method pads a string with another string:
```js
let text = "5";
let padded = text.padStart(4,"x");
//xxx5
```
```js
let text = "5";
let padded = text.padStart(4,"0");
//0005
```
- The padStart() method is a string method.

- To pad a number, convert the number to a string first.

```js
let numb = 5;
let text = numb.toString();
let padded = text.padStart(4,"0");
//0005
```


## JavaScript String padEnd()
- The padEnd() method pads a string with another string:

```js
let text = "5";
let padded = text.padEnd(4,"x");
// 5xxx
```
```js
let text = "5";
let padded = text.padEnd(4,"0");
// 5000
```
- The padEnd() method is a string method.

- To pad a number, convert the number to a string first.

```js
let numb = 5;
let text = numb.toString();
let padded = text.padEnd(4,"0");
//5xxx
```


## JavaScript String charAt()
- The charAt() method returns the character at a specified index (position) in a string:

```js
let text = "HELLO WORLD";
let char = text.charAt(0); //  H

```
## JavaScript String charCodeAt()
- The charCodeAt() method returns the unicode of the character at a specified index in a string:

```js
let text = "HELLO WORLD";
let char = text.charCodeAt(0); //72
```

## JavaScript String split()
- A string can be converted to an array with the split() method:

```js
let text = "How are you doing today?";
const myArray = text.split(" ");
//  How,are,you,doing,today?
```