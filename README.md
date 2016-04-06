The aim of this gist is to provide information (at least the ES proposal) around babel plugins, all in one page to avoid going back and forth in Babel documentation and ES propoals and specs. It's grouped by stages so you know what you have when you use babel stages.

I usually don't use Babel stages as I don't use all the features of all stages, I include the plugins of the features I want, it makes my npm install quicker and small and it helps tracking which feature I have.

It's interesting as I think that most people don't need stage 0 and there are some stage 0 proposals like [function bind](https://github.com/zenparsing/es-function-bind) that I've never heard of and I've never seen a tutorial about them.

If you have useful links about each feature, open a PR or an issue.

# [Stage 0](https://github.com/babel/babel/blob/master/packages/babel-preset-stage-0/index.js)

### [Do expressions](https://babeljs.io/docs/plugins/syntax-do-expressions/) ([`babel-plugin-transform-do-expressions`](https://github.com/babel/babel/tree/master/packages/babel-plugin-transform-do-expressions))
```js
// from https://gist.github.com/DmitrySoshnikov/de4727f57c5acc17e9469d1a91743125

let x = 10;

let a = do {
  if (x == 10) {
    100;
  } else if (x > 10) {
    200;
  } else {
    300;
  }
};

console.log(a); // Prints '100'
```
  - [Proposal](http://wiki.ecmascript.org/doku.php?id=strawman:do_expressions)
  - [More info](https://gist.github.com/DmitrySoshnikov/de4727f57c5acc17e9469d1a91743125)
  - Very handy for conditions inside JSX: https://github.com/reactjs/react-future/issues/35#issuecomment-120009203

### [Function bind](https://babeljs.io/docs/plugins/syntax-function-bind/) ([`babel-plugin-transform-function-bind`](https://github.com/babel/babel/tree/master/packages/babel-plugin-transform-function-bind))
```js
// from https://babeljs.io/blog/2015/05/14/function-bind

import { map, takeWhile, forEach } from "iterlib";

getPlayers()
::map(x => x.character())
::takeWhile(x => x.strength > 100)
::forEach(x => console.log(x));

// equivalent

import { map, takeWhile, forEach } from "iterlib";

let _val;
_val = getPlayers();
_val = map.call(_val, x => x.character());
_val = takeWhile.call(_val, x => x.strength > 100);
_val = forEach.call(_val, x => console.log(x));
```
  - [Proposal](https://github.com/zenparsing/es-function-bind)
  - [Babel blog post](https://babeljs.io/blog/2015/05/14/function-bind)


# [Stage 1](https://github.com/babel/babel/blob/master/packages/babel-preset-stage-1/index.js)

### [Class constructor call](https://babeljs.io/docs/plugins/transform-class-constructor-call/) ([`babel-plugin-transform-class-constructor-call`](https://github.com/babel/babel/tree/master/packages/babel-plugin-transform-class-constructor-call))
```js
// from http://www.2ality.com/2015/10/call-constructor-esprop.html

class Point {
  constructor(x, y) {
    this.x = x;
    this.y = y;
  }
  call constructor(x, y) {
    return new Point(x, y);
  }
}

let p1 = new Point(1, 2); // OK
let p2 = Point(3, 4); // OK
```
  - [Proposal](https://github.com/tc39/ecma262/blob/master/workingdocs/callconstructor.md)
  - [ECMAScript proposal: function-callable classes](http://www.2ality.com/2015/10/call-constructor-esprop.html)

### [Class properties](https://babeljs.io/docs/plugins/transform-class-properties/) ([`babel-plugin-transform-class-properties`](https://github.com/babel/babel/tree/master/packages/babel-plugin-transform-class-properties))
```js
// from https://github.com/jeffmo/es-class-fields-and-static-properties

class MyClass {
  myProp = 42;
  static myStaticProp = 21;

  constructor() {
    console.log(this.myProp); // Prints '42'
    console.log(MyClass.myStaticProp); // Prints '21'
  }
}
```
  - [Proposal](https://github.com/jeffmo/es-class-fields-and-static-properties)

### [Decorators](https://babeljs.io/docs/plugins/transform-decorators/) ([`babel-plugin-transform-decorators`](https://github.com/babel/babel/tree/master/packages/babel-plugin-transform-decorators))
```js
// from https://github.com/wycats/javascript-decorators/blob/master/README.md

// Simple class decorator
@annotation
class MyClass { }

function annotation(target) {
   target.annotated = true;
}

// Class decorator
@isTestable(true)
class MyClass { }

function isTestable(value) {
   return function decorator(target) {
      target.isTestable = value;
   }
}

// Function decorator
class C {
  @enumerable(false)
  method() { }
}

function enumerable(value) {
  return function (target, key, descriptor) {
     descriptor.enumerable = value;
     return descriptor;
  }
}
```
  - [Proposal](https://github.com/wycats/javascript-decorators/blob/master/README.md)
  - [Bug](https://phabricator.babeljs.io/T2645)
  - Apparently not supported, you have to include [`babel-plugin-transform-decorators-legacy`](https://github.com/loganfsmyth/babel-plugin-transform-decorators-legacy)

### [Export extensions](https://babeljs.io/docs/plugins/transform-export-extensions/) ([`babel-plugin-transform-export-extensions`](https://github.com/babel/babel/tree/master/packages/babel-plugin-transform-export-extensions))
```js
// from https://github.com/leebyron/ecmascript-more-export-from

export * as ns from "mod";
export v from "mod";
```
  - [Proposal](https://github.com/leebyron/ecmascript-more-export-from)

# [Stage 2](https://github.com/babel/babel/blob/master/packages/babel-preset-stage-2/index.js)

### [Trailing function commas](https://babeljs.io/docs/plugins/syntax-trailing-function-commas/) ([`babel-plugin-syntax-trailing-function-commas`](https://github.com/babel/babel/tree/master/packages/babel-plugin-syntax-trailing-function-commas))
```js
// from https://github.com/jeffmo/es-trailing-function-commas

function clownPuppiesEverywhere(
  param1,
  param2, // Next parameter that's added only has to add a new line, not modify this line
) { /* ... */ }
 
clownPuppiesEverywhere(
  'foo',
  'bar',
);
```
  - [Proposal](https://github.com/jeffmo/es-trailing-function-commas)
  - [Spec](http://jeffmo.github.io/es-trailing-function-commas/)

### [Object rest spread](https://babeljs.io/docs/plugins/transform-object-rest-spread/) ([`babel-plugin-transform-object-rest-spread`](https://github.com/babel/babel/tree/master/packages/babel-plugin-transform-object-rest-spread))
```js
// from https://github.com/sebmarkbage/ecmascript-rest-spread

// Rest properties
let { x, y, ...z } = { x: 1, y: 2, a: 3, b: 4 };
x; // 1
y; // 2
z; // { a: 3, b: 4 }

// Spread properties
let n = { x, y, ...z };
n; // { x: 1, y: 2, a: 3, b: 4 }
```
  - [Proposal](https://github.com/sebmarkbage/ecmascript-rest-spread)
  - [Spec](https://github.com/sebmarkbage/ecmascript-rest-spread/blob/master/Spec.md)
  
# [Stage 3](https://github.com/babel/babel/blob/master/packages/babel-preset-stage-3/index.js)

### [Async to generator](https://babeljs.io/docs/plugins/transform-async-to-generator/) ([`babel-plugin-transform-async-to-generator`](https://github.com/babel/babel/tree/master/packages/babel-plugin-transform-async-to-generator))
```js
// from http://babeljs.io/docs/plugins/transform-async-to-generator/

async function foo() {
  await bar();
}

// equivalent
var _asyncToGenerator = function (fn) {
  ...
};
var foo = _asyncToGenerator(function* () {
  yield bar();
});
```
  - [Proposal](https://github.com/tc39/ecmascript-asyncawait)

### [Exponentiation operator](https://babeljs.io/docs/plugins/transform-exponentiation-operator/) ([`babel-plugin-transform-exponentiation-operator`](https://github.com/babel/babel/tree/master/packages/babel-plugin-transform-exponentiation-operator))
```js
// from https://github.com/rwaldron/exponentiation-operator

// x ** y

let squared = 2 ** 2;
// same as: 2 * 2

let cubed = 2 ** 3;
// same as: 2 * 2 * 2


// x **= y

let a = 2;
a **= 2;
// same as: a = a * a;

let b = 3;
b **= 3;
// same as: b = b * b * b;
```
  - [Proposal](https://github.com/rwaldron/exponentiation-operator)
  - [Spec](http://rwaldron.github.io/exponentiation-operator/)
  - [The Exponentiation Operator in Babel](https://blog.mariusschulz.com/2015/11/24/the-exponentiation-operator-in-javascript#the-exponentiation-operator-in-babel)
