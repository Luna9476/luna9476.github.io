---
title: Javascript Generator Functions
layout:     post
author: Luna
date:       2022-05-05
catalog: true
tags:
    - frontend
---

A generator is a function that generates a sequence of values, but not all at once, on a per request basis instead.
We ask a generator for value, and the generator will return value or notify there is no more values.

When we call a gnerator function, it doesn't execute, but creates an object called iterator.

```javascript
function* WeaponGenerator() {
    yield "w1";
    yield "w2";
}

const weaponIterator = WeaponGenerator(); // it returns an iterator
```

Then we can use the iterator to control the execution of the generator.
```javascript
const result1 = weaponIterator.next(); // {value: w1, done: false}
```

When the next() is called, the generator executes until it reach the `yield` keyword that produces an intermediary result, and return a new object encapsulates the result and tells us whether the work is done.

Then we call next() again, it will wake up the generator from the suspension, and the generator continues where it left off, executing code until another `yield` is met and produces intermediary value.
```javascript
const result2 = weaponIterator.next(); // {value: w2, done: false}
```

If we call next() the third time, since there is no more code to execute, the generator returns object with undefined value and set done to true.
```javascript
const result3 = weaponIterator.next(); // {value: undefined, done: true}
```
## Using generators

### Using generators to generate ids
```javascript
        function* idGenerator() {
            var count = 0
            while (true) {
                count += 1
                yield count;
            }
        }

        let idIterator = idGenerator();
        const ninja1 = {id: idIterator.next().value}
        const ninja2 = {id: idIterator.next().value}
        const ninja3 = {id: idIterator.next().value}
        

        console.log(ninja1.id);
        console.log(ninja2.id);
        console.log(ninja3.id);
```

### Dom Traversal
We can also use it to traverse through dom nodes.

Assume we have a html page like below:

```html
    <div id="subTree">
        <form>
            <input type="text" />
        </form>
        <p>paragraph</p>
        <span>Span</span>
    </div>
```

If we use a callback function to log all nodes while traversing html page, we need to pass in the callback function as traverse function's parameter, the code will be like:
```javascript
function traverse(element, callback) {
    callback(element);
    element = element.firstElementChild;
    while (element) {
        traverse(element, callback);
        element = element.nextElementSibling;
    }
}
const subTree = document.getElementById("subTree");
traverse(subTree, function(element) {
    console.log(element.nodeName);
});
```

If we use generator, the code will be like below. We don't need to pass the callback function into traverse function, instead, we can let traverse as a generator function, and go through the itertor it generates, continually call next()(which is done by let..of...) to traverse the nodes.
```javascript
function* traverse(element) {
    yield element;
    element = element.firstElementChild;
    while (element) {
        yield* traverse(element);
        element = element.nextElementSibling;
    }
}
const subTree = document.getElementById("subTree");

for (const element of traverse(subTree)) {
    console.log(element.nodeName);
}
```
## Communicating with a generator

Besides sending values as generator function arguments (as line 8), we can passing values while calling next() (as line 10).
The passed value of next() will be the value of the `yield` expression where last suspended. 

In this case, we pass `Hanzo` into the generator, and the code was suspended at the first yield (line 2) before, so the value will be the `yield("Hattori " + action)` value, then will be assigned to the variable `imposter`.
```javascript
function* NinjaGenerator(action) {
    const imposter = yield("Hattori " + action);

    console.log(imposter);
    yield("Yoshi (" + imposter + ")" + action);
}

const ninjaIterator = NinjaGenerator("skulk");
console.log(ninjaIterator.next().value);

const result2 = ninjaIterator.next("Hanzo"); // send "Hanzo" back to imposter
console.log(result2.value);
```