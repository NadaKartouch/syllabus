![](https://img.shields.io/badge/status-ready-green.svg)
![Draft lesson](https://img.shields.io/badge/status-draft-darkred.svg)

# Array methods and callbacks
# JavaScript Core II - 1

The most useful built in methods in JavaScript are the `Array.prototype`
methods. Every array has access to these methods (because Arrays are created by
the `Array` constructor function they inherit the the properties of
`Array.prototype`).
**What we will learn today?**

Of particular use are the `Array` methods that enable you to _iterate_ over an
array. We've covered iteration already when we learnt how to use `for` loops.
Well, I have some amazing news for you - you will probably never need to write a
`for` loop again!

* [Objects](#objects)
* [Objects Get and Set](#objects-get-and-set)
* [More complex objects](#more-complex-objects)
* [Object methods](#object-methods)
* [Arrays of Objects](#arrays-of-objects)
* [Object.Keys()](#objectkeys)
---

Let's take a look at `Array.prototype.forEach` first. This is pretty much a
straight replacement for `for` loops.
> Please make sure you're working on the [js-exercises repo](https://github.com/CodeYourFuture/js-exercises) **Week 4** during this class.

```js
var myArr = [1, 2, 3];
## Objects

myArr.forEach(function(item) {
  console.log(item);
});
Objects in the real world have properties that describe how they are unique. Your laptop, for example, has a brand (Lenovo/Apple etc.), a screen size (13/15 inch), RAM (8/16GB) etc.

// 1
// 2
// 3
How would we describe the above laptop as a JavaScript object?

```js
var laptop = {
    brand: "Lenovo",
    screenSize: 13,
    isTouchscreen: true
};
```

OOOOF! Wasn't that glorious?! Much nicer than writing a `for` loop! So how
exactly does this work? `forEach` _iterates_ over each item the array. For each
item is calls a function - the one that was provided as an parameter to
`forEach`.
Useful words to remember when talking about objects:
- **object literal**: anything that has a set of `{...}` around a set of properties is an object literal
- **property** or **key**: `brand`, `screenSize` and `isTouchScreen` are properties/keys of the object
- **values**: `"Lenovo"`, `13` and `true` are values of the object's properties

## Callback functions
## Objects Get and Set

Functions that are provided as parameters to another function are called
_callback functions_. Often we will write these functions inside the function
call like did in the `forEach` example, but we can also pass in reference to an
already defined function:
### Getting the value of an object's property

Let's take one of the objects we looked at earlier..

```js
function callback(item) {
  console.log(item);
}
var laptop = {
    brand: "Lenovo",
    screenSize: 13,
    isTouchscreen: true
};
```

myArr.forEach(callback);
> Try to `console.log(laptop)`. The output might depend on your environment!

To find out the value of an object's property, you can use the dot notation..

```js
console.log(laptop.brand);
```

Whether you define your function beforehand or write it straight into the
function call will depend on whether you intend on re-using that callback again.
You can also use the bracket notation (although this is rarely used, it's good to know):

> Exercise
```js
console.log(laptop['brand']);
```

> Let's create a function called `average` that receives an array of numbers.
> Implement the function using a `forEach` method calculate the average of all
> `numbers` passed in and return it.
### Setting the value of a property

## More array methods
Similar to reading, if we want to set a property:

Previously we've used for loops to create new versions of an array doing
something like this:
```js
laptop.brand = "Apple";
```

It's strongly recommended you always use the same **type** when re-assigning an object's property (if it was a string before, keep it a string - and so on).

```js
var arr = [1, 2, 3];
var newArr = [];
var laptop = {
    brand: "Lenovo",
    screenSize: 13,
    isTouchscreen: true
};

for (var i = 0; i < arr.length; i++) {
  var current = arr[i];
  newArr.push(current + 1);
}
// DON'T DO THIS
laptop.screenSize = "15 inch";

console.log(newArr); // [2,3,4]
// OK TO DO
laptop.screenSize = 15;
```

There are several methods on `Array.prototype` that can be used for this sort of
task.
## More Complex Objects
 Object properties can even be assigned other objects or variables too. The example below shows an object with keys that have been assigned a variable, an array, and an object.

The most popular method is `.map()`, which does the following:
```js
var kittenName = "Feathers";

* iterates over the array it is called on
* calls a callback function on every iteration
* passes in the current array item and its index to the callback function
* uses the returned value from the callback function to populate a new array
* returns the new array
var kitten = {
    name: kittenName,
    toyCollection: ['blue ball', 'green ball', 'hoover box'],
    favoriteLocation: {
        roomName: 'Living room',
        napPlace: 'window',
        idealTemperatureCelsius: 24
    }
};
```

That sounds like a lot but once you use `.map()` a few times it'll begin to feel
more intuitive. Let's try it and see if we can refactor the for loop example:
## Object Methods

Besides having specific properties, objects in the real world can also do things. For example, a computer can display something on the screen, a person can say their names etc... In Javascript, we do this using 'methods'. A method is a function attached to a particular object. You have already used some predefined methods before, for example *toUpperCase()* on a string or *filter()* on an array.

```js
var arr = [1, 2, 3];
var newArr = arr.map(function(num) {
  return num + 1;
});
console.log(newArr); // [2,3,4]
var athlete = {
    name: 'Usain Bolt',
    goldMedals: 25,
    sayHi: function() {
        return "Hi everybody!";
    }
};
```

Another useful array method is `.filter()`. It works in a similar way to map
except that rather than return a value in the callback function, you return
`true` or `false` depending on whether you want the current item to be included
in the new array. Returning `true` means that you want to keep the item,
returning `false` means it should be omitted.
How do we call this method? 

Let's create a new array with only numbers greater than 5:
```js
athlete.sayHi(); // returns "Hi everybody!"
```

An object method can also rely on the other properties of the object to do more complex calculation. To reference the current object in the body of the method, we will use the keyword *this*. Let's take an example.

```js
var arr = [1, 2, 3, 4, 5, 6, 7, 8, 9];
var newArr = arr.filter(function(num) {
  return num > 5;
});
console.log(newArr); // [6,7,8,9]
var athlete = {
    name: 'Usain Bolt',
    goldMedals: 25,
    sayName: function() {
        return "My name is " + this.name;
    }
};

athlete.sayName(); // returns "My name is Usain Bolt"
```

> Remember: Most array methods do not change the current array, they return a
> new array. Check the MDN documentation for the array method if you are not
> sure about this.
Knowing this, you can have methods which modify existing properties of your object.

## Chaining methods
```js
var athlete = {
    name: 'Usain Bolt',
    goldMedals: 25,
    winNewMedal: function() {
        this.goldMedals = this.goldMedals + 1;
    }
};

If we want to apply more than one array method to an array we might try
something like this, creating an intermediate variable after each
transformation.
athlete.winNewMedal();
console.log(athelete.goldMedals); // prints "26"
```

As methods are just functions attached to objects, they can also take parameters.

```js
var arr = [1, 2, 3];
var arrMapped = arr.map(function(num) {
  return num + 1;
});
var arrFiltered = newArr.filter(function(num) {
  return num > 5;
});
var athlete = {
    name: 'Usain Bolt',
    goldMedals: 25,
    silverMedals: 7,
    winNewMedal: function(medal) {
        if (medal === "gold") {
            this.goldMedals = this.goldMedals + 1;
        } else {
            this.silverMedals = this.silverMedals + 1;
        }
    }
};

athlete.winNewMedal("silver");
console.log(athlete.goldMedals); // prints "25"
console.log(athlete.silverMedals); // prints "8"
```

This can get quite awkward though, especially when you have to think of a
variable name for each stage. Thankfully there is a much simpler way. We can
_chain_ methods together:
## Arrays of objects

In the past weeks, you've learned about using arrays of numbers, arrays of string etc... In the following, we will learn how to use arrays of objects.

```js
var newArr = [1,2,3,4,5,6]
  .map(function (num) {
    return num + 1;
  })
  .filter(function (num) {
    return num > 5;
  });
  console.log(newArr); // [6,7]
var kitten1 = {
    name: 'Fluffy',
    weeksOld: 2
};

var kitten2 = {
    name: 'Megatron',
    weeksOld: 1
};

var kitten3 = {
    name: 'Billy',
    weeksOld: 5
};

var kittens = [kitten1, kitten2, kitten3];
```

There's nothing magical happening here. This works because:
You can also use all the functions for arrays that you learned before: find, some, every, filter, map, forEach... As an example, we want to filter all the kittens who are less than 3 weeks old:

* the array methods are returning new arrays
* every array has access to all the array methods on `Array.prototype`
```js
function isYoungerThan3Weeks(kitten) {
    return kitten.weeksOld <= 3;
}

As soon as an array is returned by an array method we can call another array
method on the return value.
kittens.filter(isYoungerThan3Weeks);    // returns [kitten1, kitten2];
```

> Exercise
What if we want to get an array of all the kitties names?

> Transform the following array [4,5,3,6,7,8,9,1,2] by 1) sorting it, 2)
> doubling each number, and 3) filtering numbers less than 10 Write named
> functions that can be used as callbacks.
```js
function getName(kitten) {
    return kitten.name;
}

# Homework
kittens.map(getName);   // returns ["Fluffy", "Megatron", "Billy"]
```
## Object.Keys()

Since we started JavaScript, we have used `console.log` to print things to our console.

In week 2 and 3, you learned about array methods like `.map()`, `.length()`.

These are what we call built-in methods, and they're part of the JavaScript language. Someone else created these methods, and we can use them in our code.

Like arrays, objects have build in methods that can help us. In this lesson, we will learn about `Object.keys()`. This method goes into our object, and returns the object property names as an array.

Here is an example output for using `.keys()`:

```js
var footballClubs = {
  chelsea_fc: 'England',
  fc_barcelona: 'Spain',
  ac_milan: 'Italy'
};

console.log(Object.keys(footballClubs));
// prints [ 'chelsea_fc', 'fc_barcelona', 'ac_milan' ]
```

{% include "./homework.md" %}
