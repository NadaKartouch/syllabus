# JavaScript Core: in the Browser
![Draft lesson](https://img.shields.io/badge/status-draft-darkred.svg)

![](https://img.shields.io/badge/status-ready-green.svg)
# JavaScript Core II - 2

** What we will learn today?**
**What we will learn today?**

* [DOM](#dom)
* [Events](#browser-events)

* [JS In the Browser (The DOM)](#js-in-the-browser)
* [Callbacks and Asynchronous Functions](#callbacks-and-asynchronous-functions)
* [Promises](#promises)
* [AJAX](#ajax)
---

## The DOM
> Please make sure you're working on the [js-exercises repo](https://github.com/CodeYourFuture/js-exercises) **Week 5** during this class.

Your webpages are made up of a bunch of HTML elements, nested within each other
(parents and children). In JavaScript we have access to this "DOM" object
(Document Object Model) which is actually a representation of our webpage that
JavaScript can work with.
## JS in the Browser

In the browser the DOM is represented by the `window.document` object, which can
also be accessed directly using `document`. We can use it to get information
about the page loaded into the browser, query the content of the page and edit
it. You can see full details of the functionality
[here](https://developer.mozilla.org/en-US/docs/Web/API/Document).
Up until now we've been using `console.log` to see the results of our code running, because it allows us to focus on writing code and seeing the results instantly. But JavaScript was not meant to be run in `console.log`: it was meant to make web pages pages dynamic.

### Querying
Lots of websites are powered by JavaScript today, and some (like Facebook) cannot function at all without it: it's become that important to the look and feel of the website.

The DOM offers a lot of useful functions we can use to find elements on the
page. Here are some we'll be using today:
### The DOM

```js
// gets an Element with id 'submit'
var element = document.getElementById("submit");
```
Your webpages are made up of a bunch of HTML elements, nested within each other (parents and children). But JavaScript doesn't know about any of that.

Thankfully, in JavaScript we have access to this "DOM" object (Document Object Model) which is actually a representation of our webpage that JavaScript can work with.

Here are two examples, HTML and then JavaScript, of how the DOM might look like:

```html
<html>
    <body>
        <h1> Welcome! </h1>
        <p> Hello world! </p>
    </body>
</html>
```

`getElementById` accepts an id string as argument and returns an `Element` from
the document with a matching id. If no matching `Element` is found the function
returns `null`.



```js
// get an HTMLCollection containing elements with class 'link'
var links = document.getElementsByClassName("link");
```
```js
var document = {
    body: {
        h1: "Welcome",
        p: "Hello world!"
    }
};
```

`getElementsByClassName` takes a string containing one or more classes and
returns an `HTMLCollection`, which is an array-like object containing all
elements whose class attributes match the string. We can pass multiple classes
as an argument to query for elements matching all classes.

```js
// get an Element with id 'submit'
var form = document.getElementById("myform");
// get an HTMLCollection containing elements with class 'red'
// which are children of the 'form' element
var inputs = form.getElementsByClassName("red");
The DOM offers a lot of useful functions we can use to find elements on the page. Here are some we'll be using today:

```js
    document.querySelector('#mainHeader');
    document.querySelectorAll('p');


```

`getElementsByClassName` can be called on individual `elements` as well as the
top-level `document` object. When calling `getElementsByClassName` on an
`element`, the method will query only the children of the `element` rather than
the entire `document`

Both `.querySelector` and `querySelectorAll` accept a CSS selector as an input.
`.querySelector` selects only the first element it finds, `querySelectorAll` selects all elements (it returns an array).

Once you retrieve an element using `.querySelector`, you can attach an **event** to it. An event is any action that can be performed on that element. For now, we will just use the **click** event:

```js
var elements = document.getElementsByTagName("div"); // or:
var elements = someElement.getElementsByTagName("a");


    var myButton = document.querySelector('#myButton');
    myButton.addEventListener("click", alertSomething);

    function alertSomething() {
        alert("Something");
    }
```

Much like `getElementsByClassName`, `getElementsByTagName` allows us to query
for elements using the tag name. `getElementsByTagName` also returns
`HTMLCollection` and can be called on `element`s as well as `document`.
You will notice in the example example that we passed a second argument to `addEventListener`. That second argument is the **function** that we want to invoke when that event has happened.

All of the above calls return a live reference, which means that the objects
will be automatically updated with all changes since the query.

> **Exercise**:
>
> * [ ] Clone the repo from HTML and CSS class into new `bikes` directory. `git
>   clone git@github.com:dmitrigrabov/bikes-for-refugees.git bikes`
> * [ ] Once cloned run `npm install` to download the dependencies:
> * [ ] Implement `getTitle`, `getNumberOfBikes`, `getAllButtonText`,
>   `getNavLinksText` in `src/functions.js` using above methods to get all tests
>   passing using `npm test`:

### Query selector

The above selector functions are available in all browsers, but can be somewhat
inflexible for example in situations that require complex lookups. Modern
browsers have

The elements returned by `document.querySelector` have the same properties as a normal HTML element: for example, you can get access to their css **styles**.

```js
    var myElement = document.querySelector('#myElement');
    myElement.style.backgroundColor = 'red';
```

Using the `document`, you can also create new elements. These elements will not appear until you append them as a child of another element though:

```js
document.querySelector("#mainHeader");
document.querySelectorAll("p");
    var paragraph = document.createElement('p'); // here we're just creating it, element is not visible yet
    myElement.appendChild(paragraph); // now the element is added to our view, but it's empty
```

Both `.querySelector` and `querySelectorAll` accept a CSS selector as an input.
`.querySelector` selects only the first element it finds, `querySelectorAll`
selects all elements and returns a `NodeList`, which is a collection of `Nodes`
(not an array). Unlike the selectors in the previous section, these functions
return static results. That means any changes in the DOM will NOT result in
updates to the elements.
`document.createElement` accepts as an input any element type. So for example `document.createElement('article')` will create a new article element.


> **Exercise**:
>
> * [ ] Rewrite solutions to previous exercise using `querySelector` and
>   `querySelectorAll`. You may need to look up documentation for `NodeList`.
You can then change the text displayed inside elements using the `innerText` property:

### DOM manipulation
```js
    paragraph.innerText = "How are you?"; // now we can see the text displaying on the screen
```

We can use the DOM to edit elements. For example the `textContent` property of
elements can used to read as well as set the text contents of an element.

```js
var x = document.querySelector(".jumbotron h1");
console.log(x.textContent); // Bikes for Refugees
x.textContent = "Something else";
We've been using `document.querySelector` to retrieve a single element.
To retrieve an array of multiple elements (that match a specific class name for example, or a specific tag) we use `document.querySelectorAll`.

```js
    //change the background of all the paragraph items on our page
    var paragraphs = document.querySelectorAll('p');
    for(var i=0; i<paragraphs.length; i++) {
        paragraphs[i].style.backgroundColor = "blue";
    }
```

Similarly, `innerHTML` property of elements can be used to get the HTML content
of an element as well as
We've learned that `style` and `innerText` are properties of DOM elements. Image tags can also have `width` and `height`.


While it's really easy to change styles directly on elements using the `style` property, it is not usually a good idea to mix JavaScript and CSS (see separation of concerns in the first lesson). To solve this, we can use the `className` property to set the class for an element instead of changing its styles directly:

```js
var x = document.querySelector(".jumbotron h1");
x.innerHTML = "<strong>" + x.textContent + "</strong>";
//before: <div id="myContainer"></div>
var container = document.querySelector('#myContainer');
container.className = "largeBlock";
//after: <div id="myContainer" class="largeBlock"></div>
```

We can also access the `style` property of elements and update various
properties
To get the text from an Input field:

```js
var elements = document.querySelectorAll(".btn-primary");

elements.forEach(function(element) {
  element.style.backgroundColor = "red";
});
var updateTitleBtn = document.querySelector('#updateTitleBtn');

updateTitleBtn.addEventListener('click', function() {
    var inputBox = document.querySelector('#titleInput');
    var title = inputBox.value;

    var titleElement = document.querySelector('#lessonTitle');
    titleElement.innerText = title;
    inputBox.value = title;
});
```

Please note the use of camelCase style attribute names
The above waits for click on a button. When the button is clicked, it gets the input box element (`inputBox` variable).
To get the entered text from it, we use the `value` property: `var title = inputBox.value`.

We can also check it exists, read, change and remove attributes of elements
using `hasAttribute`, `getAttribute()`, `removeAttribute` and `setAttribute`
## Callbacks and Asynchronous Functions

We have already seen callback functions - in the Array methods `forEach`, `map`, `filter` etc. They are functions that are passed as parameter to another function.

Callbacks have another purpose as **asynchronous** functions. For these type of functions, the callback is called once another function has completed. This allows you to run some other code while you're waiting for something to finish.

```js
var elements = document.querySelectorAll("a");

elements.forEach(element => {
  if (element.hasAttribute("href")) {
    var href = element.getAttribute("href");
    element.setAttribute("href", "https://google.com");
  }
});
function finished() {
  console.log("The task has finished");
}

function thingThatTakesALongTime(callback) {
  //... Task that takes a long time to complete

  callback(); // This is where the 'console.log' happens
}

// Pass the function to 'thingThatTakesALongTime' just like a normal variable
thingThatTakesALongTime(finished);
```

What will above code do?
So far all of the callbacks you have been using have been **synchronous**. This means your code is executed one line at a time, at the same time, in order. Asynchronous code is not executed in order, and can run at any time, in any order.


> **Exercise**:
>
> Use above functions to
> * [ ] place `-` around the text in the navbar links
> * [ ] convert links in 'Upcoming Events' section to italic using `<i>` tag
> * [ ] make `Learn more` links green
> * [ ] Ensure all tests for above pass

### Creating and inserting elements

We can use `document.createElement(tagName)` method to create a new element and
`document.createTextNode(text)` to create new text contents. The elements
created can be manipulated just like the elements above, but the changes will
not be visible until we insert the new element into the DOM.

We can insert elements into other elements using `element.appendChild` or
`element.insertBefore`. For example.

```html
<div id="parent">
  <p>some content</p>
</div>
```

An example of this in real life, are phone calls and text messages.

* Phone calls are `synchronous` because you can't (really) do anything while the
  other person is speaking. You are always waiting for your turn to respond
* Text messages are `asynchronous`. When you send a text, you can go away and do
  something else, until the other person responds.

A simple example of an asynchronous function is `setTimeout`. This allows you to run a function after a
given time period. The first argument is the function you want to run, the
second argument is the `delay` (in milliseconds)

```js
// Separate function definition
function myCallbackFunction() {
  console.log("Hello world!");
}
setTimeout(myCallbackFunction, 1000);

// Inline function
setTimeout(function() {
  console.log("Goodbye world!");
}, 500);
```

Now let's use a timeout and a callback function together:

```js
var spanNode = document.createElement("span");
var textNode = document.createTextNode("hello");
spanNode.appendChild(textNode);

var parentNode = document.getElementById("parent");
parentNode.appendChild(spanNode);
function finished(result) {
    console.log('Finished! The result is: ' + result)
}

function startWork(stuff, callback) {
    console.log('Starting! The stuff is: ', stuff)
    setTimeout(function() {
        callback(stuff + 50)
    }, 1000)
}

startWork(50, finished)
```

What do you think above code will do?
>**Exercises**
>
> * Using setTimeout, change the background colour of the page after 5 seconds (5000 milliseconds).
> * Update your code to make the colour change _every_ 5 seconds to something different. Hint: try searching for `setInterval`.
> ![](http://g.recordit.co/g2EqBccNzh.gif)
> Complete the exercises in this [CodePen](https://codepen.io/textbook/pen/LrxgMN?editors=1010)

`insertBefore` is a bit more complicated.
## Promises

```js
var insertedNode = parentNode.insertBefore(newNode, referenceNode);
```
Promises are a new(ish) feature of JavaScript. They allow for
writing easier to understand code when dealing with asynchronous functions.
![](http://exploringjs.com/es6/images/promises----promise_states_simple.jpg)




Here `insertedNode` is the the node being inserted, that is `newNode`.
`parentNode` is the the parent of the newly inserted node. `newNode` is the node
to be inserted and `referenceNode` is the node before which newNode is inserted.
Promises are more "abstract" than anything we have covered so far. They are a data structure that represents some result that is going to happen in the future. The result starts off as being unknown (pending) as the code has not completed yet. The result can then move to be successful (fulfilled) or failed (rejected).

> **Exercise**:
>
> * [ ] Use the inspector to examine the navbar
> * [ ] Using `createElement` etc. create a new navbar item link 'Code Your Future'
>   which links to `https://codeyourfuture.io/`. It should have same structure
>   as the other links
> * [ ] Insert it at the end of the navbar
> * [ ] Ensure all tests for above pass
The API is very simple. When you have a Promise, you can attach a `.then`
method with a callback and/or a `.catch` method with a callback. If the promise is successful, then the function
in the `.then` callback is called. If it fails, then the `.catch` callback is
called.

## Resources


```js
// Call a function that returns a Promise
var myPromise = functionThatReturnsAPromise();

1. [DOM: Document](https://developer.mozilla.org/en-US/docs/Web/API/Document)
2. [MDN: DOM Examples and explanation](https://developer.mozilla.org/en-US/docs/Web/API/Document_Object_Model/Examples)
myPromise.then(function(value) {
  console.log("success: " + value);
});



## Browser events

myPromise.catch(function(value) {
  console.log("fail:" + value);
});
```

Browser events are actions that take place on our web page. They could be user
triggered such as a mouse being clicked, a key being pressed or a form
submitted. Alternatively, they could be triggered by the system such as a
resource being loaded or an error occurring.
The `.then` and `.catch` methods can be chained, like with Array methods:

We can subscribe to those events by registering an `eventHandler` to perform a
certain action when an event is detected. For example, we may want to update a
letter count on a text input when a user types or we may want to perform
validation on a form before submitting it.
```js
myPromise.then(function(value) {
  console.log("success: " + value);
})
.catch(function(value) {
  console.log("fail: " + value);
})
```

For each event subscription we will need 3 things:
You can even return a Promise from within a `.then` callback, and keep chaining on more `.then` callbacks. This allows you to process part of the value and keep passing it along the chain:

1. `target` - this is the object where we are listening for events on. For
   example, it could be a link on which we would like to listen to for clicks.
1. `eventType` - as the name suggests, this is the type of event we ar listening
   for. There are dozens of possible events (see
   [here](https://developer.mozilla.org/en-US/docs/Web/Events) for the full
   list). Common ones include . `click` - mouse click . `submit` - form submit .
   `keydown` - keyboard key being pressed . `mouseenter` - a mouse cursor being
   moved onto an element . `change` - value of a form input changing
1. `eventHandler` - A function that we want to execute when the event is
   detected
```js
// myPromise resolves with a value of 50
myPromise.then(function(value) {
  console.log(value) // Logs: 50
  return Promise.resolve(value + 50); // Returns a new Promise
})
.then(function(value) {
  console.log(value) // Logs: 100
})
```

To subscribe to the actual event we use the `addEventListener` method of our
`target` element like below
We will look at some common functions that return a Promise in a bit, but you can also create your own Promise. This example shows a Promise being "resolved" (successful):

```js
var myButton = document.querySelector("#myButton");
myButton.addEventListener("click", alertSomething);
```js
var myPromise = new Promise(function(resolve, reject) {
  // Do some work in this function
  resolve(100); // Resolves the Promise with the value 100
});
```

function alertSomething() {
  alert("Something");
}
```
This example shows a Promise being "rejected" (failed):

```js
var myPromise = new Promise(function(resolve, reject) {
  // Do some work in this function
  reject(50) // Rejects the Promise with the value 50
});
```

In the above code `myButton` is the target on which we listen to for `click`
events and call the event handler `alertSomething` when the click is detected.
> **Exercises**
> 
> Complete the exercises in [this CodePen](https://codepen.io/fortythieves/pen/QOYgWb?editors=1010)

> **Exercise**:
>
> * [ ] Set a click listener on the donate buttons and increment the donated bikes
>   counter with each click ( no tests )
## AJAX

### Event object
### Client/Server architecture

Just knowing that an event has happened is not particularly useful in most
cases. Usually, we will want to know more about what exactly happened such as
the coordinates of a mouse `click` or the new `value` of an input after it has
changed.
A **server** is a device or program that provides functionality to other programs or devices. There are database servers, mail servers, game servers, etc. The vast majority of these servers are accessed over the internet. They can take the form of industrial server farms that provide a service to millions of users (used by Facebook, Google, etc.), to personal servers for storing your files.




Keep in mind that different event types will have characteristics that are
specific to them. For example, `key` events will have a `event.char` property
indicating the key that was pressed. `mouse` events will have `event.clientX`
and `event.clientY` properties indicating the location of the mouse event on the
screen, where (0,0) is the top left hand corner in the browser.
The server communicates with **clients**. A client can be a web browser, a Slack app, your phone, etc.

Every `event` object has a `.preventDefault()` which when called will prevent
the default action of the event from being triggered. This is particularly
useful to intercepting events and altering the behaviour when needed. For
example, we can call `event.preventDefault()` on a `submit` event if the data in
the form is not valid.
Client–server systems use the **request–response** model: a client sends a request to the server, which performs some action and sends a response back to the client, typically with a result or acknowledgement.

We can find out which element the event was triggered on from the `event.target`
property.
![](client-server.png)

> **Exercise**:
>
> * [ ] Prevent clicks on links from triggering a url change in the browser and
>   instead `console.log` the coordinates of the click as well as the text
>   inside the link
### HTTP Requests

### Bubbling
A server stores the data, and the client (other programs or computers) requests data or sends some of its own. But how do they talk to each other?

> **Together**:
>
> * Let's place a `click` listener on the `.jumbotron` element and `console.log`
>   the `event`
> * What happens when we click on the buttons?
**For the client and the server to communicate they need an established language (a protocol)**. Which is what HTTP (Hypertext Transfer Protocol) is for. It defines the methods you can use to communicate with a server and indicate your desired actions on the resources of the server.

Most events, though not all, have a default behaviour know as `bubbling` which
results in events being propagated to the target element's parents. That means
an event listener placed on the parent will be triggered after the event
listener placed on the child. Why is this behaviour desired?
There are two main types of requests: **GET** and **POST**.

We can distinguish between the elements on which the event was triggered vs the
element on which the event was detected.


| Request type  | Description   |
| ------------- |:-------------:|
| GET          | Ask for a specified resource (e.g. show me that photo) |
| POST          | Send content to the server (e.g. post a photo) |






* `event.target` is the element on which received the initial event
* `event.currentTarget` is the element on which the event listener detected the
  event

In some cases we may want to prevent an event from bubbling up. We can do so by
calling the `stopPropagation` method on the event. Once it has been called, any
event handlers placed by parent elements will not be triggered.

> **Together**:
>
> * Let's prevent clicks on 'Volunteer' button from bubbling up to above
>   listener using `stopPropagation`

# Resources

1. [Introduction to browser events](https://javascript.info/introduction-browser-events)
2. [Events](https://developer.mozilla.org/en-US/docs/Web/Events)


HTTP is the language of the internet. In our case we're using Javascript, but you can send HTTP requests with other laguages as well.

### What is AJAX?

AJAX is a technique for implementing client-server communication in the browser.

Typically, the server holds the data, and only sends it to the client (web page) when there's a request. AJAX requests are sent after the page has loaded, usually in response to an action by the user. For example when the user clicks a button, some JavaScript will trigger an AJAX request to fetch data.

### Introduction to Fetch and asynchronous code

**fetch** is a way of creating HTTP requests in JavaScript.

```js
fetch('https://codeyourfuture.herokuapp.com/api/hello')
    .then(function(response) {
        return response.text(); // or response.json()
    })
    .then(function(text) {
        console.log(text); // Print 'Hello CodeYourFuture!'
    });
```

{% include "./homework.md" %}
