#  Deep Diff
[![Build Status](https://travis-ci.org/dispix/deep-diff.svg?branch=master)](https://travis-ci.org/dispix/deep-diff) [![npm](https://badge.fury.io/js/return-deep-diff.svg)](https://www.npmjs.com/package/return-deep-diff)
[![Coverage Status](https://coveralls.io/repos/github/dispix/deep-diff/badge.svg?branch=master)](https://coveralls.io/github/dispix/deep-diff?branch=master)

Function returning an object representing the difference between two objects. The function is immutable-compliant as it does not affect the arguments.

This is a fork of [deep-diff](https://github.com/dispix/deep-diff) by [dispix](https://github.com/dispix) with some extra code to allow obj2 to add keys/objects that 
are not found in obj1.

## Installation

```
npm install -S return-deep-diffs
```

## Usage

```js
import deepDiff from 'return-deep-diffs'

const objOne = {
  a: 1,
  b: {
    c: 2,
    d: 3
  },
  e: 4
}

const objTwo = {
  a: 1,
  b: {
    c: 2,
    d: 30,
    f: 50
  },
  e: 40
}

console.log(deepDiff(objOne, objTwo))
/*
returns:
  {
    b: {
      d: 30
    },
    e: 40
  }
*/

console.log(deepDiff(objOne, objTwo, true))
/*
returns:
  {
    b: {
      d: 30
      f: 50
    },
    e: 40
  }
*/
```

The two objects must share the exact same structure, which is defined by the first object. If a key is present in the second but not the first object, it will not be present in the diff object unless `keepNewKeys` equals `true`.
The function does not mutate neither the first nor the second object.
