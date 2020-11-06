# babel-plugin-tree-shaking-import

[![NPM version](https://img.shields.io/npm/v/babel-plugin-tree-shaking-import.svg)](https://npmjs.org/package/babel-plugin-tree-shaking-import)
[![Build Status](https://travis-ci.org/ElementUI/babel-plugin-component.svg?branch=master)](https://travis-ci.org/ElementUI/babel-plugin-component)
[![Coverage Status](https://coveralls.io/repos/github/QingWei-Li/babel-plugin-component/badge.svg?branch=master)](https://coveralls.io/github/QingWei-Li/babel-plugin-component?branch=master)

## Install

```shell
npm i babel-plugin-tree-shaking-import -D

or

yarn add babel-plugin-tree-shaking-import -D
```

## Example

Converts

```javascript
import { Button } from 'element-ui';
```

to

```javascript
var button = require('element-ui/lib/button.js');
require('element-ui/packages/theme-chalk/src/button.scss');
```

## Usage

Use with babel-loader

```javascript
module.exports = {
  module: {
    rules: [
      {
        test: /\.m?js$/,
        exclude: /(node_modules|bower_components)/,
        use: {
          loader: 'babel-loader',
          options: {
            plugins: [
              [
                'tree-shaking-import',
                {
                  libraryName: 'element-ui',
                  libDir: 'lib',
                  styleLibraryDir: 'packages',
                  styleLibraryName: 'theme-chalk/src',
                  style: false,
                  ext: '.scss',
                },
              ],
            ],
          },
        },
      },
    ],
  },
};
```

Use with nuxt.config.js

```javascript
module.exports = {
  babel: {
    plugins: [
      [
        'tree-shaking-import',
        {
          libraryName: 'element-ui',
          libDir: 'lib',
          styleLibraryDir: 'packages',
          styleLibraryName: 'theme-chalk/src',
          style: false,
          ext: '.scss',
        },
      ],
    ],
  },
};
```

### More options see [babel-plugin-component](https://github.com/ElementUI/babel-plugin-component)
