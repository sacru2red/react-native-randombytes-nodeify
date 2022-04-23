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
// or
yarn add react-native-randombytes-nodeify
```
2. install peerDependencies and babel-plugin
```
npm install react-native-randombytes
npm install --save-dev babel-plugin-module-resolver
// or
yarn add react-native-randombytes
yarn add --dev babel-plugin-module-resolver
```
3. add a babel plugin to babel.config.js
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

### Etc.
+ If you try importing 'randombytes' before installing this package, you should clear react-native cache
```
npm start -- --reset-cache
```

## Usage

```js
// linking steps
// "randombytes" => "react-native-randombytes-nodeify" => "react-native-randombytes"'s randomBytes
var randomBytes = require('randombytes');

// get 4 random bytes
const rand = randomBytes(4)

// asynchronous API
randomBytes(4, (err, bytes) => {
  // bytes is a Buffer object(4 random bytes)
  console.log(bytes.toString('hex'))
})
```

## And We can use node packages!