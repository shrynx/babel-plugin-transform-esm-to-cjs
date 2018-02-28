[![JavaScript Style Guide](https://img.shields.io/badge/code_style-standard-brightgreen.svg)](https://standardjs.com)
[![code style: prettier](https://img.shields.io/badge/code_style-prettier-ff69b4.svg?style=flat-square)](https://github.com/prettier/prettier)
[![Conventional Commits](https://img.shields.io/badge/Conventional%20Commits-1.0.0-yellow.svg)](https://conventionalcommits.org)

# babel-plugin-transform-esm-to-cjs

> a babel plugin for lightweight conversion from esm to cjs without much ceremony

## Purpose

transform basic `import` and `export` syntax of esm to cjs

```js
import a from './a'
```

to

```js
var a = require('./a')
```

---

```js
export default a
```

to

```js
module.exports = a
```

---

```js
export { default as a } from './a'
export { default as b } from './b'
```

to

```js
module.exports = {}
module.exports.a = require('./a')
module.exports.b = require('./b')
```

## Usage

add as plugin to your babel configuration

```js
{
  //...
  "plugins": [
    // ...
    "babel-plugin-transform-esm-to-cjs"
  ]
}
```

## Use case

This plugin was made for developing library to be used with node.js or with bundler that can consume cjs
