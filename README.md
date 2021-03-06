# nodejs-tail

Simple NodeJs implementation of tail command.
## Install

```js
yarn add nodejs-tail
```

## Syntax

`new Tail(filename, options)`

- _filename_ - file to watch
- _options_ - [chokidar](https://github.com/paulmillr/chokidar) watcher options, with next values **always everwritten**: `{
      alwaysStat: true,
      ignoreInitial: false,
      persistent: true,
    }`. That is required to work similar to `tail` command.

## Example

```js
const Tail = require('nodejs-tail');

const filename = 'some.log';
const tail = new Tail(filename);

tail.on('line', (line) => {
  process.stdout.write(line);
})

tail.on('close', () => {
  console.log('watching stopped');
})

tail.watch();

setTimeout(() => {
  tail.close();
}, 3000);
```


MIT License. Copyright (c) 2017-2020 Vladimir Kuznetsov
