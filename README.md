# Deepen your understanding of closures, and improve your process for understanding code

## Setup: 5 mins

* If you haven't got node installed, run `brew install node`.

* Create a file called `investigate.js` and put this code in it:

```
console.log("hello!");
```

* Run `node investigate.js`.  You should see `hello!` written to the console.

* Create a file called `log.txt` and save it.

* Optional, but recommended.  Move your windows around so you have `log.txt`, `investigate.js` and your terminal on screen at the same time.

## Demo: 15 mins

I'll take the code sample below and demonstrate my process of trying to answer the question in the comment.  I'll keep a written log.  Each log entry will have this format:

```
* What I did:
* Why:
```

My demo code sample:

```
// What output does this code produce? Why?

function bar() {
  return foo;
  foo = 10;
  function foo() {}
  var foo = '11';
};

console.log(bar());
```

## Workshop: 30 mins

* Split into pairs.  One person is the investigator, the other is the observer.

* The investigator pastes Code Sample 1 (below) into `investigate.js`.  They try to answer the question in the comment.  They investigate by changing and running the code sample.

* As the investigator investigates, they keep a detailed written log.  Each log entry has this format:

```
What I did:
Why:
```

* The observer doesn't join in with the investigation.  But If they don't understand what the investigator is doing or why they are doing something, they ask the investigator to write more detailed log entries.

* When the investigator has an answer to the question in the comment, they explain it to the observer.

* Once the investigation is over, the pair swap roles and move onto the next code sample.

* Do the code samples in order.  They build on each other. It's fine not to make it through all of them.

* Save your logs!

## Plenary: 15 mins

We'll come back together, collect some of our log entries on the board and discuss the successful and less successful processes we use to understand code.

## Code samples

### Code sample 1

```js
var variableA = 0;

function functionA() {
  // Can I use variableA on this line? Why?
};

functionA();
```

### Code sample 2

```js
function functionA() {
  var variableA = 0;
};

functionA();

// Can I use variableA on this line? Why?
```

### Code sample 3

```js
var variableA = 1;

function functionA() {
  variableA = 2;

  // What value does variableA have on this line? Why?
};

functionA();

// What value does variableA have on this line? Why?
```

### Code sample 4

```js
var variableA = 1;

function functionA(variableA) {
  // What value does variableA have on this line? Why?
};

functionA(2);
```

### Code sample 5

```js
var variableA = 1;

function functionA() {
  var variableA = 2;
};

functionA();

// What value does variableA have on this line? Why?
```

### Code sample 6

```js
var variableA = 1;

if (true) {
  var variableA = 2;
}

// What value does variableA have on this line? Why?
```

### Code sample 7

```js
// What is printed when you run this code? Why?

function makeAddingFunction(numberToAdd) {
  function addingFunction(numberToAddTo) {
    return numberToAdd + numberToAddTo;
  };

  return addingFunction;
};

var add4 = makeAddingFunction(4);

console.log(add4(10));
```

### Code sample 8

```js
// What is printed when you run this code? Why?

function makeAddingFunction(numberToAdd) {
  function addingFunction(numberToAddTo) {
    return numberToAdd + numberToAddTo;
  };

  numberToAdd = 6;

  return addingFunction;
};

var add4 = makeAddingFunction(4);

console.log(add4(10));
```

### Code sample 9

```js
// What is printed when you run this code? Why?

var http = require("http");

function makeRequest() {
  var host = "google.com";

  http.get({ host: host }, function() {
    console.log("Successful request to " + host);
  });

  host = "somewhere else!";
};

makeRequest();
```

### Code sample 10

```js
// WTF?

var http = require('http');

function makeRequests() {
  var urls = ["google.com"];

  for (var i = 0; i < urls.length; i++) {
    http.get({ host: urls[i] }, function() {
      console.log("Successful request to " + urls[i]);
    });
  }
};

makeRequests();
```

### Code sample 11

```js
// What is printed when you run this code? Why?

var http = require('http');

function makeRequests() {
  var urls = ["google.com"];

  urls.forEach(function(url) {
    http.get({ host: url }, function() {
      console.log("Successful request to " + url);
    });
  });
};

makeRequests();
```
