
Create script2.js file and add: 
```
const largeNumber = 356;

export default largeNumber;
```
Then in script.js:

```

import largeNumber from 'script2.js'

const a = largeNumber;
const b=5;
setTimeout(()=> {
	console.log(a + b);
	console.log(__dirname);
}, 3000)
```
This throws an error because ES6 import statements is not implemented in node.js yet. There are work arounds to this, you can add packages. There is another way: 

```

In script.js set largeNumber using require path :

```
const largeNumber = require ('./script2.js')

const a = largeNumber;
const b=5;
setTimeout(()=> {
	console.log(a + b);
	console.log(__dirname);
}, 3000)

```
In script2.js: 
```
const largeNumber = 356;

module.exports = {
 largeNumber: largeNumber
 };
```

If run in node get the following:
```
Rob@RobPC MINGW64 ~/Documents/coding/zeromasterywebdev/node (master)
$ node script.js
[object Object]5
C:\Users\Rob.000\Documents\coding\zeromasterywebdev\node
```
Because now we have exported global object. If change script.js as follows:

```
const script2 = require ('./script2.js')

const a = script2.largeNumber;
const b=5;
setTimeout(()=> {
	console.log(a + b);
	console.log(__dirname);
}, 3000)

```
Then if run in node.js: 
```
$ node script.js
361
```
Can change variable name and it still works: 
```
```
const c = require ('./script2.js')

const a = c.largeNumber;
const b=5;
setTimeout(()=> {
	console.log(a + b);
	console.log(__dirname);
}, 3000)

```

