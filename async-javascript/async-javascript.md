# ES5 . ES6 . ES7
### Asynchronous JavaScript

![inline fit](images/js.jpg)

---

## __Callbacks__
## __Promises__
## __Async/Await__
## __Generators__

---

## Callbacks - ES5

__Example 1:__

```javascript
function handler(request, response) {
    User.get(request.user, function(err, user) {
        if (err) {
            response.send(err);
        } else {
            Notebook.get(user.notebook, function(err, notebook) {
                if (err) {
                    return response.send(err);
                } else  {
                    doSomethingAsync(user, notebook, function(err, result) {
                        if (err) {
                            response.send(err);
                        } else {
                            response.send(result);
                        }
                    });
                }
            });
        }
    });
}
```

---

## Callbacks - ES5

__Example 2:__

```javascript
require('request')
    .get('http://www.google.com', function(err, response) {
         if (err) {
             console.error(err);
          } else {
              require('fs')
              .writeFile('google.html', response.body, function(err) {
                  if (err) {
                      console.error(err);
                  } else {
                      console.log('wrote file');
                  }
              });
          }
    });
```

---

## Promises - ES6

__Example 2:__

```javascript
require('request-promise')
  .get('http://www.google.com')
  .then((response) => {
      return require('fs-promise').writeFile('google.html', response);
  })
  .then(() => {
      console.log('wrote file');
  })
  .catch((err) => {
      console.log(err);
  });
```

---

## Promises - ES6

__Example 1:__

```javascript
function(request, response) {
    let user, notebook;

    User.get(request.user)
      .then((aUser) => {
          user = aUser;
          return Notebook.get(user.notebook);
      })
      .then((aNotebook) => {
          notebook = aNotebook;
          return doSomethingAsync(user, notebook);
      })
      .then((result) => {
          response.send(result);
      })
      .catch((err) => {
          response.send(err);
      });
}
```

---

## Async/Await - ES7

### __Description__

When async function is called, it [returns a promise](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/async_function#Description).  When the async function returns a value, the promise will be resolved with the returned value.  When the async function throws an exception or some value, the promise will be rejected with the thrown value.

Async function can contain [await](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/await) expression, that pauses the execution of the async function and waits for the passed promise's resolution, and resumes the async function's execution and returns the resolved value.

---

## Async/Await - ES7

__A Simple Example__

```javascript
function resolveAfter2Seconds(x) {
  return new Promise(resolve => {
    setTimeout(() => {
      resolve(x);
    }, 2000);
  });
}

async function add1(x) {
  let a = resolveAfter2Seconds(20);
  let b = resolveAfter2Seconds(30);

  return x + await a + await b;
}

add1(10).then(v => {
  console.log(v);  // prints 60 after 2 seconds.
});
```

---

## Async/Await - ES7

__A Slight Tweak__

```javascript
function resolveAfter2Seconds(x) {
  return new Promise(resolve => {
    setTimeout(() => {
      resolve(x);
    }, 2000);
  });
}

async function add2(x) {
  let a = await resolveAfter2Seconds(20);
  let b = await resolveAfter2Seconds(30);

  return x + a + b;
}

add2(10).then(v => {
  console.log(v);  // prints 60 after 4 seconds.
});
```

---

## Async/Await - ES7

__Let's get back to the previous example.__

__Example 1:__

```javascript

async function something(request, response) {
    try {
      let user = await User.get(request.user);
      let notebook = await Notebook.get(user.notebook);
      let result = await doSomethingAsync(user, notebook);

      response.send(result);
    } catch(err) {
      response.send(err);
    }
}
```
---

## Async/Await - ES7

__What does async do?__

Essentially, it wraps the return value of the function in a promise. Under the hood it is more or less using [generators](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/function*), but all of that is hidden away behind this simple syntax.

-

```javascript
await "Hello!"
```

What if it's a non-promise? Will this work?

---

## Generators - ES6

Generators are functions which can be exited and later re-entered. Their context (letiable bindings) will be saved across re-entrances.

-

__Syntax__

```javascript
function* name([param[, param[, ... param]]]) {
   statements
}
```

---

## Generators - ES6

Calling a generator function does not execute its body immediately; an [iterator](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Iteration_protocols#iterator) object for the function is returned instead. When the iterator's [next()](#) method is called, the generator function's body is executed until the first [yield](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/yield) expression, which specifies the value to be returned from the iterator or, with [yield*](#), delegates to another generator function.

---

## Generators - ES6

__A Simple Example__

```javascript
function* idMaker(){
  let index = 0;
  while(index < 3)
    yield index++;
}

let gen = idMaker();

console.log(gen.next().value); // 0
console.log(gen.next().value); // 1
console.log(gen.next().value); // 2
console.log(gen.next().value); // undefined
```

---

## Generators - ES6

__Another Example__

```javascript
function* anotherGenerator(i) {
  yield i + 1;
  yield i + 2;
  yield i + 3;
}

function* generator(i){
  yield i;
  yield* anotherGenerator(i);
  yield i + 10;
}

let gen = generator(10);

console.log(gen.next().value); // 10
console.log(gen.next().value); // 11
console.log(gen.next().value); // 12
console.log(gen.next().value); // 13
console.log(gen.next().value); // 20
```
---

## Generators - ES6

Generators are mostly used with [promises](https://developer.mozilla.org/en/docs/Web/JavaScript/Reference/Global_Objects/Promise).

```javascript
{
  "userId": 1,
  "id": 1,
  "title": "sunt aut facere repellat provident",
  "body": "suscipit recusandae consequuntur expedita"
}

const co = require('co');
const fetch = require('node-fetch');

co(function* (){
  let uri = 'https://jsonplaceholder.typicode.com/posts/1';
  let response = yield fetch(uri);
  let post = yield response.json();

  console.log('Title: ', post.title); // sunt aut facere repellat provident
});
```
---

## How to start using Async/Await?

### [http://babeljs.io](http://babeljs.io/)

![inline 55%](images/babel.png)

```javascript
// .babelrc
{
  "presets": ["es2015", "es2017"]
}
```

---

## And a lot of study.

* [Handle asynchronous non-blocking I/O in JavaScript](http://sebastianmetzger.com/handle-asynchronous-non-blocking-io-in-javascript)
* [Iterators and Generators](https://developer.mozilla.org/en/docs/Web/JavaScript/Guide/Iterators_and_Generators)
* [Async Function](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/async_function)
* [From Callbacks to Promises to Generators to Async/await](https://medium.com/@rdsubhas/es6-from-callbacks-to-promises-to-generators-87f1c0cd8f2e)
* [The Hidden Power of ES6 Generators](https://medium.com/javascript-scene/the-hidden-power-of-es6-generators-observable-async-flow-control-cfa4c7f31435)
* [Generators in JavaScript](https://youtu.be/ategZqxHkz) [Video]
* [Async Programming in ES7](https://youtu.be/lil4YCCXRYc) [Video]

---

## Hopefully, this didn't blow your mind.

![inline fit](images/mind-blown.gif)

---

# Thank You
