<h1 align="center">typescript-case-convert</h1>
<p>
  <a href="https://codecov.io/gh/filipemir/typescript-case-convert">
    <img src="https://codecov.io/gh/filipemir/typescript-case-convert/branch/main/graph/badge.svg?token=AYHMX8GX4V"/>
  </a>
  <a href="https://badge.fury.io/js/typescript-case-convert">
    <img src="https://badge.fury.io/js/typescript-case-convert.svg" alt="npm version" height="18" />
  </a>
  <img alt="npm bundle size" src="https://img.shields.io/bundlephobia/minzip/typescript-case-convert?style=flat">
  <img alt="npm type definitions" src="https://img.shields.io/npm/types/typescript-case-convert?style=flat">
  <img alt="GitHub package.json dependency version (dev dep on branch)" src="https://img.shields.io/github/package-json/dependency-version/filipemir/typescript-case-convert/dev/typescript">
  <a href="https://github.com/filipemir/typescript-case-convert#readme" target="_blank">
    <img alt="Documentation" src="https://img.shields.io/badge/documentation-yes-brightgreen.svg" />
  </a>
  <a href="https://github.com/filipemir/typescript-case-convert/graphs/commit-activity" target="_blank">
    <img alt="Maintenance" src="https://img.shields.io/badge/Maintained%3F-yes-green.svg" />
  </a>
  <a href="https://github.com/filipemir/typescript-case-convert/blob/main/LICENSE" target="_blank">
    <img alt="License: Apache--2.0" src="https://img.shields.io/github/license/filipemir/typescript-case-convert" />
  </a>
</p>

typescript-case-convert converts object keys between `camelCase`, `snake_case`, and `PascalCase` while preserving Typescript type information, code completion, and type validation. See tests for detailed conversion tests.

> This repo is a fork of [ts-case-convert](https://github.com/RossWilliams/ts-case-convert), which no longer seems to be maintained

## Usage

```typescript
const camel = objectToCamel({
  hello_world: 'helloWorld',
  a_number: 5,
  an_array: [1, 2, 4],
  null_object: null,
  undef_object: undefined,
  an_array_of_objects: [{ a_b: 'ab', a_c: 'ac' }],
  an_object: {
    a_1: 'a1',
    a_2: 'a2',
  },
});

type CheckCamel = typeof camel.anArrayOfObjects[0]['aB']; // -> 'string'
const ab: CheckCamel = camel.anArrayOfObjects[0]['aB']; // -> valid
console.log(camel.anArrayOfObjects.aB); // -> 'ab'

const snake = objectToSnake({
  helloWorld: 'helloWorld',
  aNumber: 5,
  anArray: [1, 2, 4],
  nullObject: null,
  undefObject: undefined,
  anArrayOfObjects: [{ aB: 'ab', aC: 'ac' }],
  anObject: {
    A1: 'a_1',
    A2: 'a_2',
  },
});

type CheckSnake = typeof snake.an_array_of_objects[0]['a_b']; // -> 'string'
const ab: CheckSnake = snake.an_array_of_objects[0]['a_b']; // -> valid
console.log(snake.an_array_of_objects.a_b); // -> 'ab'
```

## Run tests

```sh
yarn run test
```

## Documentation

See [tests](./test/caseConvert.test.ts).
