![](https://img.shields.io/badge/status-review-orange.svg)

# Node 1

**What we will learn today?**

* [What is a server?](#what-is-a-server)
* [Node and its ecosystem](#node-and-its-ecosystem)
* [HTTP](#http)
* [Express](#express)
* [Workshop](#workshop)

---

## What is a server?

Servers are computer programs that receive requests from other programs, the
_clients_ and send back a response e.g share data, information or hardware and
software resources.

### ...and what is a server in plain English?

A server is a computer program. Its job is to send and receive data.

Let's take a website for example. A website is just a collection of HTML and CSS
files, images, maybe some javascript files. When you type a website address in
your browser's address bar, the browser (client) sends a **request** to the
server that lives at that address. The browser asks the server to give it the
files it needs to display the website properly.

![Server flow](https://files.gitter.im/heron2014/FiiK/server.png)

## Node and its ecosystem

> [Node.js®](https://nodejs.org/en/) is a **JavaScript runtime** built on
> Chrome's **V8 JavaScript engine**. Node.js uses an **event-driven**,
> **non-blocking** I/O model that makes it lightweight and efficient.

## What is it used for?

* web servers, so creating dynamic websites
* set up a local web development environment
* easier to build desktop applications with Electron: Slack, Visual Code, Atom
* some of the biggest companies use Node.js in production: Netflix, Walmart,
  IBM, etc.
* JavaScript everywhere (used to be PHP, Python, JavaScript, MySQL, Apache, now
  JavaScript full stack)

## A simple Node.js server

### Simple server\*\*

```js
const http = require("http");

const server = http.createServer(function(req, res) {
  res.end("Hello World!");
});

server.listen(5000);

console.log("Node.js web server at port 5000 is running..");
```

## HTTP

> It is a protocol that browser and the server uses to talk to each other

![HTTP](../assets/http_diagram.png)

Read more on Mozilla's
[An overview of HTTP](https://developer.mozilla.org/en-US/docs/Web/HTTP/Overview)

## Express

[Express](http://expressjs.com/) is one of the most widely-used frameworks for
Node.js. It simplifies base features of Node.js, making it easier and faster to
build your application's backend. Learning Express gives you a great foundation
for becoming a Node.js developer.

## Workshop

Buckle up and start the [API workshop](./api-workshop.md).

## Group Research Topics

* Security: (https, same origin, cookies, xss etc..)
* Performance: Request lifecycle (from browser to server and back), Performance
  considerations and optimisations
* HTTP and REST: (headers, status codes, Cookies, REST)
* Node internals: Node event loop, Node core modules, async/sync (non-blocking
  operations)

## Resources

Take a look at the following links to learn more about Node.js.

* Read: [The art of node](https://github.com/maxogden/art-of-node/#the-art-of-node)
* Read: [Node Resources](https://node.cool#resources)

More about HTTP:
[Tutsplus tutorial](https://code.tutsplus.com/tutorials/http-headers-for-dummies--net-8039)

More about JSON:

* https://en.wikipedia.org/wiki/JSON
* https://developer.mozilla.org/en/docs/Web/JavaScript/Reference/Global_Objects/JSON/parse
* https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/JSON/stringify

Heroku:

* [Deploying from Git](https://devcenter.heroku.com/articles/git)
* [Deploying Node Apps](https://devcenter.heroku.com/articles/getting-started-with-nodejs#set-up)

{% include "../../others/escalation-policy.md" %}
