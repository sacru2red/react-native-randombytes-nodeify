# react-native-randombytes-nodeify

randombytes nodeify for react-native (metro bundler), react-native-randombytes wrapper

randombytes for dependencies on react-native runtime

## What is this
```js
// many packages use "randombytes"
var randomBytes = require('randombytes');

// and "react-native-randombytes" package support like this and similar API
import { randomBytes } from 'react-native-randombytes'
// or
var { randomBytes } = require('react-native-randombytes');

// install this package and set your project
// now, you can use randombytes same node syntax
var randomBytes = require('randombytes');
```

## Installation
1. add package
```
npm install react-native-randombytes-nodeify
yarn add react-native-randombytes-nodeify
```
2. add a babel plugin
```js
module.exports = {
  presets: ['module:metro-react-native-babel-preset'],
  plugins: [
    [
      require.resolve('babel-plugin-module-resolver'),
      {
        alias: {
          randombytes: './node_modules/react-native-randombytes-nodeify',
        },
      },
    ],
  ],
};
```

## Usage

```js
var randomBytes = require('randombytes');

// get 4 random bytes
const rand = randomBytes(4)

// asynchronous API
// uses iOS-side SecRandomCopyBytes
randomBytes(4, (err, bytes) => {
  // bytes is a Buffer object(4 random bytes)
  console.log(bytes.toString('hex'))
})
```

## And We can use node packages!