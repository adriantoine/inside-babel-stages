The aim of this gist is to provide information (at least the ES proposal) around babel plugins, all in one page to avoid going back and forth in Babel documentation and ES propoals and specs. It's grouped by stages so you know what you have when you use babel stages.

I usually don't use Babel stages as I don't use all the features of all stages, I include the plugins of the features I want, it makes my npm install quicker and small and it helps tracking which feature I have.

It's interesting as I think that most people don't need stage 0 and there are some stage 0 proposals like [function bind](https://github.com/zenparsing/es-function-bind) that I've never heard of and I've never seen a tutorial about them.

If you have useful links about each feature, open a PR or an issue.

# [Stage 0](https://github.com/babel/babel/blob/master/packages/babel-preset-stage-0/index.js)

### [Do expressions](https://babeljs.io/docs/plugins/syntax-do-expressions/) ([`babel-plugin-transform-do-expressions`](https://github.com/babel/babel/tree/master/packages/babel-plugin-transform-do-expressions))
  - [Proposal](http://wiki.ecmascript.org/doku.php?id=strawman:do_expressions)
  - [More info](https://gist.github.com/DmitrySoshnikov/de4727f57c5acc17e9469d1a91743125)
  - Very handy for conditions inside JSX: https://github.com/reactjs/react-future/issues/35#issuecomment-120009203

### [Function bind](https://babeljs.io/docs/plugins/syntax-function-bind/) ([`babel-plugin-transform-function-bind`](https://github.com/babel/babel/tree/master/packages/babel-plugin-transform-function-bind))
  - [Proposal](https://github.com/zenparsing/es-function-bind)
  - [Babel blog post](https://babeljs.io/blog/2015/05/14/function-bind)


# [Stage 1](https://github.com/babel/babel/blob/master/packages/babel-preset-stage-1/index.js)

### [Class constructor call](https://babeljs.io/docs/plugins/transform-class-constructor-call/) ([`babel-plugin-transform-class-constructor-call`](https://github.com/babel/babel/tree/master/packages/babel-plugin-transform-class-constructor-call))
  - [Proposal](https://github.com/tc39/ecma262/blob/master/workingdocs/callconstructor.md)
  - [ECMAScript proposal: function-callable classes](http://www.2ality.com/2015/10/call-constructor-esprop.html)

### [Class properties](https://babeljs.io/docs/plugins/transform-class-properties/) ([`babel-plugin-transform-class-properties`](https://github.com/babel/babel/tree/master/packages/babel-plugin-transform-class-properties))
  - [Proposal](https://github.com/jeffmo/es-class-fields-and-static-properties)

### [Decorators](https://babeljs.io/docs/plugins/transform-decorators/) ([`babel-plugin-transform-decorators`](https://github.com/babel/babel/tree/master/packages/babel-plugin-transform-decorators))
  - [Proposal](https://github.com/wycats/javascript-decorators/blob/master/README.md)
  - [Bug](https://phabricator.babeljs.io/T2645)
  - Apparently not supported, you have to include [`babel-plugin-transform-decorators-legacy`](https://github.com/loganfsmyth/babel-plugin-transform-decorators-legacy)

### [Export extensions](https://babeljs.io/docs/plugins/transform-export-extensions/) ([`babel-plugin-transform-export-extensions`](https://github.com/babel/babel/tree/master/packages/babel-plugin-transform-export-extensions))
  - [Proposal](https://github.com/leebyron/ecmascript-more-export-from)

# [Stage 2](https://github.com/babel/babel/blob/master/packages/babel-preset-stage-2/index.js)

### [Trailing function commas](https://babeljs.io/docs/plugins/syntax-trailing-function-commas/) ([`babel-plugin-syntax-trailing-function-commas`](https://github.com/babel/babel/tree/master/packages/babel-plugin-syntax-trailing-function-commas))
  - [Proposal](https://github.com/jeffmo/es-trailing-function-commas)
  - [Spec](http://jeffmo.github.io/es-trailing-function-commas/)

### [Object rest spread](https://babeljs.io/docs/plugins/transform-object-rest-spread/) ([`babel-plugin-transform-object-rest-spread`](https://github.com/babel/babel/tree/master/packages/babel-plugin-transform-object-rest-spread))
  - [Proposal](https://github.com/sebmarkbage/ecmascript-rest-spread)
  
# [Stage 3](https://github.com/babel/babel/blob/master/packages/babel-preset-stage-3/index.js)

### [Async to generator](https://babeljs.io/docs/plugins/transform-async-to-generator/) ([`babel-plugin-transform-async-to-generator`](https://github.com/babel/babel/tree/master/packages/babel-plugin-transform-async-to-generator))
  - [Proposal](https://github.com/tc39/ecmascript-asyncawait)

### [Exponentiation operator](https://babeljs.io/docs/plugins/transform-exponentiation-operator/) ([`babel-plugin-transform-exponentiation-operator`](https://github.com/babel/babel/tree/master/packages/babel-plugin-transform-exponentiation-operator))
  - [Proposal](https://github.com/rwaldron/exponentiation-operator)
  - [Spec](http://rwaldron.github.io/exponentiation-operator/)
  - [The Exponentiation Operator in Babel](https://blog.mariusschulz.com/2015/11/24/the-exponentiation-operator-in-javascript#the-exponentiation-operator-in-babel)
