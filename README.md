# urlgithub-to-object

A module for node.js and browsers that extracts useful properties like `user`,
`repo`, and `branch` from various flavors of GitHub URLs.


## Installation

For Node.js or Browserify usage:

```sh
npm i urlgithub-to-object
```

For bower usage:

```sh
bower install urlgithub-to-object
```

## Usage

Use whatever flavor of GitHub URL you like:

```js
const gh = require('urlgithub-to-object')

gh('github:example/business')
gh('https://github.com/example/business')
gh('https://github.com/example/business/tree/master')
gh('https://github.com/example/business/tree/master/nested/file.js')
gh('https://github.com/example/business.git')
gh('http://github.com/example/business')
gh('git://github.com/example/business.git')
gh('git+https://github.com/example/business.git')
```

Here's what you'll get:

```js
{
  user: 'example',
  repo: 'business',
  branch: 'master',
  tarball_url: 'https://api.github.com/repos/example/business/tarball/master',
  clone_url: 'https://github.com/example/business',
  https_url: 'https://github.com/example/business',
  travis_url: 'https://travis-ci.org/example/business',
  api_url: 'https://api.github.com/repos/example/business'
  zip_url: 'https://github.com/example/business/archive/master.zip'
}
```

The shorthand form lets you specify a branch:

```js
gh('github:example/business#nachos')
```

```js
{
  user: 'example',
  repo: 'business',
  branch: 'nachos',
  https_url: 'https://github.com/example/business/blob/nachos',
  tarball_url: 'https://api.github.com/repos/example/business/tarball/nachos',
  clone_url: 'https://github.com/example/business',
  travis_url: 'https://travis-ci.org/example/business?branch=nachos',
  api_url: 'https://api.github.com/repos/example/business'
  zip_url: 'https://github.com/example/business/archive/nachos.zip'
}
```

If you provide a non-GitHub URL or a falsey value, you'll get `null`.

## Test

```sh
npm install
npm test
```

[![js-standard-style](https://cdn.rawgit.com/feross/standard/master/badge.svg)](https://github.com/feross/standard)

## License

MIT
