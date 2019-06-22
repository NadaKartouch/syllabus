![Lesson in review](https://img.shields.io/badge/status-review-orange.svg)

# JavaScript Core 2
# JavaScript Core I - 2

**What we will learn today?**

* [Arrays](#arrays)
* [Objects](#objects)
* [Useful Arrays methods](#useful-array-methods)


* [Expressions](#expressions)
* [Boolean Filters](#boolean-filters)
* [Comparison operators](#comparison-operators)
* [Predicates](#predicates)
* [Conditionals](#conditionals)
* [Logical Operators](#logical-operators)
* [More Conditionals](#more-conditionals)
* [Array literals](#array-literals)
* [Array properties](#array-properties)
* [Array getters and setters](#array-getters-and-setters)
* [Array methods](#array-methods)
* [More Array methods](#more-array-methods)
* [Array map](#array-map)

---
> Please make sure you're working on the [js-exercises repo](https://github.com/CodeYourFuture/js-exercises) **Week 2** folder during this class.

## Arrays
## Expressions

If you want to store a **list of values**, declaring manually a number of
varibles becomes quickly tiresome and untenable:
In JavaScript there are **expressions** and **statements**. We will use these words frequently to describe code.

### Expression

An expression returns a value. Sometimes we will say that an expression _evaluates to_ a value.

The following are all examples of expressions:

```js
var name1 = 'Bill'
var name2 = 'Marta'
var name3 = 'Andrew'
...
1 + 1; // returns 2
("hello"); // returns "hello"
2 * 4; // returns 8
"hello" + "world"; // returns "helloworld"
```

**Arrays** to the rescue!
We can take the value produced by an expression and assign it to a variable. That line of code would be called a statement.

An Array is a native javascript data type, like the integers, strings and
boolean that you saw last week.
### Statement

It contains a ordered list of values, and each of those values can be of any
data type (even another array and objects, which you will learn about next!).
A statement is some code that performs an action. Here are some examples:

Arrays are _ordered_, which means that each value has a specific position in it.
This is very useful, as it allows us to access and interact with the single
values present in the array. They are also _mutable_, which means that values
inside them can be changed, added and removed.
```js
var sum = 1 + 1; // action: assigns result of `1 + 1` to variable `sum`
var greeting = "hello"; // action: assigns result of the expression "hello" to variable `greeting`
console.log(2 * 4); // action: logs the result of `2 * 4` to the console
sayGreeting(greeting); // action: calls the function `sayGreeting` with the parameter `greeting`
```

The syntax for an array is a number of variables separated by commas, with
square brackets and the start and end.
There are some other different types of statements that we will learn in the coming weeks.

### Exercise

You quickly find out the result of an expression by running node in a terminal window.

* Open a terminal window
* Run the command `node`
* _You have now opened a node console (also called a REPL)_
* Type an expression and press enter
* To exit the console type Ctrl+C or type the command `.exit`

Example from inside a terminal window:

```bash
$ node
> 1 + 2
3
> "hello"
'hello'
> var greeting = "hello"
undefined
> greeting
'hello'
> console.log(greeting)
hello
undefined
> .exit
$
```

> Notice how when we execute an expression the value it produces is printed below it. When we execute a statement, we see `undefined` printed below. This is because statements don't produce values like expressions, they _do something_.

* Write some more expressions in the node console
* Assign some expressions to variables
* Check the value of the variables

Further reading on using the node console: [https://hackernoon.com/know-node-repl-better-dbd15bca0af6](https://hackernoon.com/know-node-repl-better-dbd15bca0af6)

## Boolean Filters

There is a special data type in JavaScript known as a **boolean** value. A boolean is either `true` or `false`, and it should be written without quotes.

```js
["Bill", "Marta", "Andrew"][(1, 53, 135, 6, 2)][ // an array of 3 strings // an array of 5 integers
  ("Hello world", 98, true, "Rachel")
]; // an array containing different data types
var codeYourFutureIsGreat = true;
```

var myArrayOfFriends = ["Bill", "Marta", "Andrew"]; // assigning the array to a variable
### Exercise

Head over to `exercise.js` and follow the instructions in the comments.

## Comparison Operators

We can also write **expressions** that return boolean values.

Here's an expression that evaluates to a boolean.

```sh
1 > 2
```

### Interacting with the array
* Can you work out what value this expression evaluates to?

An array data type is only useful if we can interact with the values stored
within. Like other data type, arrays in Javascript have a number of methods
already defined to make our life easier.
The `>` symbol in the expression is a **comparison operator**. Comparison operators compare two values. This operator checks to see if the number on the left is bigger than the number on the right.

Let's start by defining an array of animals!
`1` is not bigger than `2` so this expression returns `false`.

## More comparison operators

```sh
>   greater than
<   less than
<=  less than or equal
>=  greater than or equal
=== same value
!== not the same value
```

### Exercise

* Open `exercise.js` and follow the instructions.
* Open a node console, and write some expressions that use comparison operators

## Predicates

**Predicate** is a fancy word for a function that returns a boolean value.

These functions are very useful because they let you test if a value satisifies certain requirements.

```js
var animals = ["tiger", "puppy", "snake", "llama"];
function isNumber(value) {
  return typeof value === "number";
}

isNumber(10); // returns true
isNumber("hello"); // returns false
```

Pretty neat! Now you have all the animals grouped together rather than having to
define them separately. One of the useful methods that we get from arrays lets
us check the number of values present in it by accessing the `length` attribute.
JavaScript programmers often give predicate functions a name that starts with a verb e.g. `isBig`, `isNegative`, `isActive`, `shouldUpdate`,

We do that with a `.`, like so:
Calling a predicate function is like asking a question: "is this value a number". The return value is the answer to your question.

## Conditionals

Like humans, computer programs make decisions based on information given to them. **Conditionals** are a way of representing these decisions in code.

For example:

* In a game, if the player has 0 lives, then the game is over
* In a weather app, if rain is forecast, a picture of rain clouds is shown

The most common type of conditional is the **if statement**.

An if statment runs some code if a condition is met. If the condition is not met, then the code will be skipped.

```js
console.log(animals.length); // 4
var isHappy = true;

if (isHappy) {
  console.log("I am happy");
}
```

We have the length, but how do you access a single value inside?
Using an _index_!
The code in paratheses - e.g. `(isHappy)` - is the condition. The condition can be _any_ expression. The following are all valid conditions:

An index is an integer, such as `0`, `1`, `2`, etc. It indicates the
position of the values inside the array. As is common in many programming
languages, indices in JavaScript arrays start with `0` --- so `0` is
the index of the first element of an Array, `1` is the index of the second
element, and so forth.
```js
// boolean value
if (true) {
  // do something
}

If you want to refer to one specific member of the array, you can do so by using
their 'index number' like so:
// variable assigned to boolean value
if (isHappy) {
  // do something
}

// equality operator returns a boolean value
if (1 + 1 === 2) {
  // do something
}

// comparison operator returns a boolean value
if (10 > 5) {
  // do something
}

// function call returns boolean value
if (greaterThan10(5)) {
  // do something
}
```

An if statement runs code when a condition is met. What if the condition is not met? Sometimes you want to run an alternative bit of code.

An **if...else statement** also runs code when the condition is _not_ met.

```js
console.log(animals[1]); // Guess the output before running the command!
var isHappy = true;

if (isHappy) {
  console.log("I am happy 😄");
} else {
  console.log("I am not happy 😢");
}
```

> Take a guess at which animal that will print out, and see if you're right.
## Logical Operators

Spoiler alert, it will print out `'puppy'`. That might seem weird, until you
remember the paragraph just before the example: arrays in Javascript are
0-indexed, which means that the first value is accessed with `animals[0]` :
There are three logical operators in JavaScript: `||` (OR), `&&` (AND), `!` (NOT).

They let you write expressions that evaluate to a boolean value.

Suppose you want to test if a number if bigger than 3 and smaller than 10. We can write this using logical operators.

```js
console.log(animals[0]); // 'tiger'
console.log(animals[1]); // 'puppy'
console.log(animals[2]); // 'snake'
console.log(animals[3]); // 'llama'
console.log(animals[4]); // undefined! the array has 4 elements, animal[5] would try to access the 5th!
var num = 10;

function satisfiesRequirements(num) {
  if (num > 3 && num < 10) {
    return true;
  }

  return false;
}
```

> **Exercise:**
>
> 1 Create an array that contains the countries of all the students in the
> class (at least five nationalities)
> 2 `console.log` the number of countries in the Array
> 3 Now, `console.log()` each country in the list
> 4 Update point 3 to work for arrays of any length (hint: use for loops and the length property)
>
> Extra points: **Don't ask a mentor - Google it!** Try googling to find the answer if you're
> stuck. Google skills are an essential part of being a developer.
We can test expressions with logical operators in a node console too:

## Objects
```sh
$ node
> var num = 10;
undefined
> num > 5 && num < 15
true
> num < 10 || num === 10
true
> false || true
true
> !true
false
> var greaterThan5 = num > 5
undefined
> !greaterThan5
false
> !(num === 10)
false
```

Now for the final data type: objects. Like arrays, they can store multiple bits
of information, except objects store the properties of something. For example,
you might want to save the name, model and colour of a car. Or the name, time
and location of a film playing at the cinema.
## More Conditionals

The syntax looks like this:
A common use of if statements is inside of functions.

```js
{
  property1: 'value1',
  property2: 'value2',
  property3: 'value3'
function getGrade(score) {
  if (score >= 80) {
    return "A";
  }
  if (score >= 60) {
    return "B";
  }
}
```

The names on the left ('property1') are known 'keys'. Any values can be given to
them: strings, booleans, integers.
You can also write this using `else if`:

### Try it out
```js
function getGrade(score) {
  if (score >= 80) {
    return "A";
  } else if (score >= 60) {
    return "B";
  }
}
```

Let's define an object that represents a person:
## Array Literals

If you ever find yourself writing code like this...

```js
var person = {
  firstName: "Nelson",
  lastName: "Mandela",
  occupation: "freedom fighter",
  age: 95,
  alive: false
};
var mentor1 = "Daniel";
var mentor2 = "Irina";
var mentor3 = "Rares";
```

We can `console.log()` the entire object, but you can also reference just one of
the properties. Run this code:
...then it's probably time to use an **array**!

Arrays are data structures that hold a list of values.

```js
console.log(person.firstName);
var mentors = ["Daniel", "Irina", "Rares"];
```

> **Exercise** Using an object representing a person, `console.log()` a sentence
> introducing the person. Print out the following:
>
> _'Hi, my name is {firstName} {lastName}. I am {age} years old, and work as a
> {occupation}.'_
>
> Hint: you can construct longer strings by adding them together. This includes
> variables. For example:
>
> ```js
> var name = "Jane";
> console.log("People call me " + name);
>
> // the previous line will print
> // 'People call me Jane'
> ```
Arrays can hold any type of value (although almost always you only have one data type per array).

## Useful array methods
```js
var testScores = [16, 49, 85];
var grades = ["F", "D", "A"];
var greetings = ["Hello, how are you?", "Hi! Nice to meet you!"];
```

### Concatenating two arrays
## Array properties

You've learned how you can add two numbers and append two strings, but how does
this work for arrays? A simple `arr1 + arr2` will not do, but there is a method
you can use: `concat()`. It is a method that you call on the array (similar to
how `console.log` is the `log` function called on `console`) and takes the array
you want to append as a parameter.
Arrays, like strings, have a `length` property.

You can check this by starting a node console in your terminal.

```sh
$ node
> var arr = [1, 2, 3];
undefined
> arr
[1, 2, 3]
> arr.length
3
```

## Array Getters and Setters

You can **get** a single value out of an array using **bracket notation**.

```sh
$ node
> var ingredients = ["Flour", "Water", "Salt"];
undefined
> ingredients[0]
Flour
> ingredients[1]
Water
> ingredients.length
3
```

Did you notice how we use `[0]` to get the first value? In programming we count starting at zero.

> The number inside of the brackets is called an **index**. Index just means the position of the item within the array.

You can also **set** a value using bracket notation and an assignment operator (`=`).

```js
var countries = ["Scotland", "Germany", "Syria"];
var moreCountries = ["Sudan", "Ethiopia", "France"];
var scores = [80, 41, 47];

countries.concat(moreCountries);
console.log(countries); // ['Scotland', 'Germany', 'Syria', 'Sudan', 'Ethiopia', 'France']
scores[2] = 29; // Change the last score
scores[3] = 51; // Add a new score
```

### Appending an element
## Array methods

If you want to append an element to an array, you can just put it after the last
existing element like so:
Do you remember how strings have special functions called methods? Don't worry if not! Here's an example to jog your memory:













```sh
$ node
> var name = "Daniel"
undefined
> name.toLowerCase()
daniel
```

Arrays also have several methods that you can use.

### `.sort()`

_An array method that sorts the values in an array into ascending alphabetical or numerical order._

```js
countries[countries.length] = "United States of America";


var unorderedLetters = ["z", "v", "b", "f", "g"];
var orderedLetters = unorderedLetters.sort();

var unorderedNumbers = [8, 5, 1, 4, 2];
var orderedNumbers = unorderedNumbers.sort();

console.log(orderedLetters); // logs [ 'b', 'f', 'g', 'v', 'z' ]
console.log(unorderedLetters); // logs [ 'b', 'f', 'g', 'v', 'z' ]

console.log(orderedNumbers); // logs [ 1, 2, 4, 5, 8 ]
console.log(unorderedNumbers); // logs [ 1, 2, 4, 5, 8 ]
```

There is another way though, which is a bit more elegant: the `push` function.
> When you call this array method it uses the array on the left side of the dot as an input, and it sorts that array also returning it. Note how both ordered and unordered arrays are sorted now!

### `.concat()`

_Adds (or concatenates) another value or array to the array._

```sh
$ node
> var arr = [1, 2, 3]
undefined
> arr.concat(4)
[1, 2, 3, 4]
> arr
[1, 2, 3]
```

Did you notice how calling the concat method did not change `arr`? This is because `concat`, like most array methods, returns a _new_ array, it does not alter the one you called the method on.

If you wan to use the array returned by calling `.concat()` you should store it in a new variable.

```js
countries.push("United States of America");
var arr = [1, 2, 3];
var newArr = arr.concat(4);

// .push can also be called with multiple parameters
countries.push("United States of America", "France");
console.log(newArr); // logs [1, 2, 3, 4]
```

> **Exercise**: Search `.slice`, `.splice` and `.pop` and tell us what they do
## More Array methods

## Resources
Let's explore some more array methods.

1. [Arrays](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array)
1. [Objects](https://developer.mozilla.org/en-US/docs/Learn/JavaScript/Objects/Basics)
1. [Strings](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String)
### `.slice()`
































_Returns a slice of the array._

You can tell `.slice()` where you want the slice to begin and end by passing it two parameters.

```sh
$ node
> var arr = [0, 1, 2, 3, 4]
undefined
> arr.slice(0, 2)
[0, 1]
> ["a", "b", "c", "d"].slice(1, 2)
['b']
```

### `.includes()`

_Returns true if a value is in the array._

```js
var mentors = ["Daniel", "Irini", "Ashleigh", "Rob", "Etzali"];

function isAMentor(name) {
  return mentors.includes(name);
}

consooe.log("Is Rukmuni a mentor?");
console.log(isAMentor("Rukmini")); // logs false
```

### `.join()`

_Returns all the array values joined together in a string. By default, this method takes no parameters and then the elements are divided with a comma `,`. If you provide it with a string parameter though, then it becomes the divider of the elements, like the example below:_

```sh
$ node
> ["H", "e", "l", "l", "o"].join();
'H,e,l,l,o'
> ["H", "e", "l", "l", "o"].join("--");
'H--e--l--l--o'
```

There is a string method `.split()`. In an interactive console try using the string `.split()` method and the array `.join()`. How could they work together?

## Array map

Imagine you have an array of names...

```js
var mentors = ["Daniel ", "irina ", " Gordon", "ashleigh "];
```

You notice that he names are not formatted consistently. To fix the array you decide you need to trim whitespace and convert to lowercase. How do you do that for every value in the array?

We can write a function that changes one name:

```js
function tidy(name) {
  return name.trim().toLowerCase();
}
```

All you need to run every name in the array through this function and update the array values. Thankfully there is an array method that does just this!

## `.map()`

_Runs every item in the array through a function and returns a new array with the values returned by the function_.

```js
var tidyMentors = mentors.map(tidy);

console.log(tidyMentors); // logs ["daniel", "irina", "gordon", "ashleigh"]
```

{% include './homework.md' %}
