#### SEP-21-2022

# CSS **Selectors** 

>## what is selector.?
>
>A CSS selector selects the HTML element(s) for >styling purpose. CSS selectors

> ## We can divide CSS selectors into five   categories
>
> 1. **Simple** selectors ( select elements based on name, id, class )
> 
> 2. **Combinator** selectors ( select elements based on a specific relationship between them )
> 
> 3. **Pseudo-class** selectors ( select elements based on a certain state )
> 
> 4. **Pseudo-elements** selectors ( select and style a part of an element )
> 
> 5. **Attribute** selectors ( select elements based on an attribute or attribute value  )

## Simple or Basic Selectors


### Element selector 

   This group includes selectors that target an HTML element such as an `<h1>` 
```css 
  h1 { 
      color:red 
     } 
``` 

 

### Universal selector  

  *Selects all elements* 
```css
*{ 
  color: green; 
 } 
```

Universal selectors can be namespaced when using @namespace. This is useful when dealing with documents containing multiple namespaces such as HTML with inline SVG or MathML, or XML that mixes multiple vocabularies. 

> 1. ns|* - matches all elements in namespace ns 
>
> 2.  *|* - matches all elements 
>
> 3. |* - matches all elements without any declared namespace 

 
###  Class selector  

1. The ***.class*** selector selects elements with a specific class attribute. 

2. To select elements with a specific class, write a period (.) character, followed by the name of the class. 

3. Select and style all elements with class="super": 

```css
.super { 
  background-color: yellow; 
} 
```

###  Id selector 

1. The id selector uses the id attribute of an HTML element to select a specific element. 

2. The id of an element is unique within a page, so the id selector is used to select one unique element! 

3. To select an element with a specific id, write a hash (#) character, followed by the id of the element. 

4. The CSS rule below will be applied to the HTML element with
  *id="para1"*  
```css
#para1 { 
  text-align: center; 
  color: red; 
} 
```

###  Grouping Selector
 
1. The grouping selector selects all the HTML elements with    the same style definitions. 

2. Look at the following CSS code (the h1, h2, and p elements have the same style definitions): 
```css
h1 { 
  text-align: center; 
  color: red; 
} 
 
h2 { 
  text-align: center; 
  color: red; 
} 
 
p { 
  text-align: center; 
  color: red; 
} 
```

It will be better to group the selectors, to minimize the code. 
```css
h1, h2, p { 
  text-align: center; 
  color: red; 
}
``` 

 

 

###  element,element Selector 

 

Select and style all `<h2>` elements AND all `<p>` elements: 

```css
h2, p { 
  background-color: yellow; 
} 
```
---
## Combinator Selectors

  A combinator is something that explains the relationship between the selectors.
>1. descendant selector (space)
>2. child selector (>)
>3. adjacent sibling selector (+)
>4. general sibling selector (~)

#### descendant selector`(space)`
1. The descendant selector matches all elements that are descendants of a specified element.
2. The following example selects all `<p>` elements inside `<div>`elements:

  ```css
  div p {
  background-color: yellow;
  }
  ```

#### child selector`(>)` 
1. The child selector selects all elements that are the children of a specified element.
 
2. The following example selects all `<p>` elements that are children of a `<div>` element.

```css
div > p {
  background-color: red;
}
```

#### Adjacent Sibling Selector`(+)`

1. The adjacent sibling selector is used to select an element that is directly after another specific element.

2. Sibling elements must have the same parent element, and "adjacent" means "immediately following".

3. The following example selects the first `<p>` element that  are placed immediately after `<div>` elements:

```css
div + p {
  background-color: yellow;
}
```

#### General Sibling Selector`(~)`
1. The general sibling selector selects all elements that are next siblings of a specified element.

2. The following example selects all `<p>` elements that are next siblings of `<div>` elements 

```css
div ~ p {
  back
  ground-color: yellow;
}
```

---

##  Pseudo-Classes Selector
1. A pseudo-class is used to define a special state of an element.

> 1. Style an element when a user mouses over it
> 2. Style visited and unvisited links differently
> 3. Style an element when it gets focus

```css
selector:pseudo-class {
  property: value;
}
```
### Anchor Pseudo-classes
```css
unvisited link

a:link {
  color: #FF0000;
}

visited link
a:visited {
  color: #00FF00;
}

mouse over link
a:hover {
  color: #FF00FF;
}

selected link
a:active {
  color: #0000FF;
}
```



### Pseudo-classes and HTML Classes
1. Pseudo-classes can be combined with HTML classes:

2. When you hover over the link in the example, it will change color:

```css
a.highlight:hover {
  color: #ff0000;
}
```
Hover on `<div>`
An example of using the :hover pseudo-class on a `<div>` element

```css
div:hover {
  backg
  round-color: blue;
}
```

### Simple Tooltip Hover
1. Hover over a `<div>` element to show a `<p>` element (like a tooltip):

2. Hover over me to show the `<p>` element.

```css
p {
  display: none;
  background-color: yellow;
  padding: 20px;
}

div:hover p {
  display: block;
}
```

### CSS - The :first-child Pseudo-class
1. The :first-child pseudo-class matches a specified element that is the first child of another element.
2. Match the first `<p>` element
In the following example, the selector matches any `<p>` element that is the first child of any element:

```css
p:first-child {
  color: blue;
}
```

3. Match the first `<i>` element in all `<p>` elements
In the following example, the selector matches the first `<i>` element in all `<p>` elements

```css
p i:first-child {
  color: blue;
}
```
4. Match all `<i>` elements in all first child `<p>` elements
In the following example, the selector matches all `<i>` elements in `<p>` elements that are the first child of another element:

```css
p:first-child i {
  color: blue;
}
```

### CSS - The :lang Pseudo-class
1. The :lang pseudo-class allows you to define special rules for different languages.

2. In the example below, :lang defines the quotation marks for `<q>` elements with lang="no":
  
```html
<html>
<head>
<style>
q:lang(no) {
  quotes: "~" "~";
}
</style>
</head>
<body>

<p>Some text <q lang="no">A quote in a 
  paragraph</q> Some text.</p>

</body>
</html>
```

### focus
1. when focus the element the class will apply. 

```html

<!DOCTYPE html>
<html>
<head>
<style>
input:focus {
  background-color: yellow;
}
</style>
</head>
<body>

<form action="/action_page.php" method="get">
  First name: <input type="text" name="fname"><br><br>
  Last name: <input type="text" name="lname"><br><br>
  <input type="submit" value="Submit">
</form>

</body>
</html>
```
---
## Pseudo-Elements-Selectors
### What are Pseudo-Elements ?
2. A CSS pseudo-element is used to style specified parts of an element.

>1. Style the first letter, or line, of an element
>2. Insert content before, or after, the content of an element

```css
selector::pseudo-element {
  property: value;
}
```

### The ::first-line Pseudo-element
1. The ::first-line pseudo-element is used to add a special style to the first line of a text.

2. The following example formats the first line of the text in all `<p>` elements

```css
p::first-line {
  color: #ff0000;
  font-variant: small-caps;
}
```

### The ::first-letter Pseudo-element
1. The ::first-letter pseudo-element is used to add a special style to the first letter of a text.

2. The following example formats the first letter of the text in all <p> elements 
```css
p::first-letter {
  color: #ff0000;
  font-size: xx-large;
}
```

### Pseudo-elements and HTML Classes
3. Pseudo-elements can be combined with HTML classes: 
 
```css
p.intro::first-letter {
  color: #ff0000;
  font-size: 200%;
}
```


### Multiple Pseudo-elements
4. Several pseudo-elements can also be combined.

5. In the following example, the first letter of a paragraph will be red, in an xx-large font size. The rest of the first line will be blue, and in small-caps. The rest of the paragraph will be the default font size and color:
  
```css
p::first-letter {
  color: #ff0000;
  font-size: xx-large;
}

p::first-line {
  color: #0000ff;
  font-variant: small-caps;
}
```

### CSS - The ::before Pseudo-element
1. The ::before pseudo-element can be used to insert some content before the content of an element.

2. The following example inserts an image before the content of each `<h1>` element:

```css
h1::before {
  content: url(smiley.gif);

}
```
### CSS - The ::after Pseudo-element
1. The ::after pseudo-element can be used to insert some content after the content of an element.

2. The following example inserts an image after the content of each `<h1>` element:

```css
h1::after {
  content: url(smiley.gif);
}
```
### CSS - The ::marker Pseudo-element
1. The ::marker pseudo-element selects the markers of list items.

2. The following example styles the markers of list items:
```css
::marker {
  color: red;
  font-size: 23px;
}
```

### CSS - The ::selection Pseudo-element
1. The ::selection pseudo-element matches the portion of an element that is selected by a user.

2. The following CSS properties can be applied to ::selection: color, background, cursor, and outline.

3. The following example makes the selected text red on a yellow background:

```css
::selection {
  color: red;
  background: yellow;
}
```
---
## Attribute Selectors

1. Style HTML Elements With Specific Attributes
2. It is possible to style HTML elements that have specific attributes or attribute values.



### CSS [attribute] Selector
1. The `[attribute]` selector is used to select elements with a specified attribute.

2. The following example selects all `<a>` elements with a target attribute
  
```css
a[target] {
  background-color: yellow;
}
```
### CSS [attribute="value"] Selector
1. The `[attribute="value"]` selector is used to select elements with a specified attribute and value.

2. The following example selects all `<a>` elements with a target="_blank" attribute:
```css
a[target="_blank"] {
  background-color: yellow;
}
```
### CSS [attribute~="value"] Selector
1. The `[attribute~="value"]` selector is used to select elements with an attribute value containing a specified word.

**2**. The following example selects all elements with a title attribute that contains a space-separated list of words, one of which is "flower"

```css
[title~="flower"] {
  border: 5px solid yellow;
}
```



### CSS [attribute|="value"] Selector
1. The `[attribute|="value"]` selector is used to select elements with the specified attribute, whose value can be exactly the specified value, or the specified value followed by a hyphen (-).
```css
[class|="top"] {
  background: yellow;
}
```
### CSS [attribute^="value"] Selector
1. The `[attribute^="value"]` selector is used to select elements with the specified attribute, whose value starts with the specified value.

2. The following example selects all elements with a class attribute value that starts with "top":
```css
[class^="top"] {
  background: yellow;
}
```
### CSS [attribute$="value"] Selector
1. The `[attribute$="value"]` selector is used to select elements whose attribute value ends with a specified value.

2. The following example selects all elements with a class attribute value that ends with "test":

```css
[class$="test"] {
  background: yellow;
}
```

### CSS [attribute*="value"] Selector
1. The `[attribute*="value"]` selector is used to select elements whose attribute value contains a specified value.

2. The following example selects all elements with a class attribute value that contains "te":

```css
[class*="te"] {
  background: yellow;
}
```

---
for more [MDN](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Selectors).







