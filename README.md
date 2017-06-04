# Node-v8.0.0
Changes and new features of Node v8.0.0

#### 1/ Say hello to `npm version 5.0.0`
- We can now use the latest version of npm v5.0.0 with Node v8.0.0

- `--save` is no longer necessary. All installs will be saved by default. You can prevent saving with `--no-save` .

- Existing npm caches will no longer be used: you will have to redownload any cached packages. There is no tool or intention to reuse old caches

 Get more [detail](http://blog.npmjs.org/post/161081169345/v500)
 
 #### 2/ Say hello to the `Node.js API (N-API)`
 - Allow native addons (modules) to be compiled once on a system and used across multiple versions of Node.js.
 
 - We now easier to maintain modules, no need to upgrade or recompile for every major Node.js release by using an ABI layer in Javascript VMs. 
 
 #### 3/ Say hello to `async_hooks`
 
 - `async_hooks` is now in nodejs core, we can use by require it :
 
 ```
      const async_hook =  require('async_hooks');
 ```
 
 - This allows developers a means of monitoring the operation of the Node.js event loop, tracking asynchronous requests and handles through their complete lifecycle

#### 4/ Say hello to the `WHATWG URL parser`

- The new URL implementation is now a fully supported, example :

```
      const myURL = new URL('/foo', 'https://example.org/');
        // https://example.org/foo
```

- API available in modern Web Browsers like Chrome, Firefox, Edge, and Safari, allowing code using URLs to be shared across environments.

#### 5/ Buffer changes

- Using old version of `Buffer(num)` will initialized memory and might have significant impact on performance

```
// Old version

const safeBuffer1 = Buffer.alloc(10);
const safeBuffer2 = new Buffer(10);
```

- New version of `Buffer(num)` will allocate Buffer instances with uninitialized memory, sample :

```
// New version in Node.js 8
const unsafeBuffer = Buffer.allocUnsafe(10);

```

#### 6/ Improved support for `Promises`

- Node.js 8.0.0 includes a new `util.promisify()` API that allows standard Node.js callback style APIs to be wrapped in a function that returns a Promise. An example use of `util.promisify()` is shown below.

```
const fs = require('fs');
const util = require('util');

const readfile = util.promisify(fs.readFile);

readfile('/some/file')
  .then((data) => { /** ... **/ })
  .catch((err) => { /** ... **/ });
```

*For more changes and features in* [`Node v8.0.0`](https://nodejs.org/en/blog/release/v8.0.0/#say-hello-to-async_hooks)
