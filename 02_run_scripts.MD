In gitBash navigate to node folder that you will need to create, then type: 
```
touch script.js 
```
To create a script.js file in current folder. Then add code: 

```
const a =4;
const b=5;

console.log(a + b);
```

Then in gitBash and type: 

```gitattributes
Rob@RobPC MINGW64 ~/Documents/coding/zeromasterywebdev/node (master)
$ node script.js
9
```

Please note it exits to return 9. It runs process.exit and exits out of file.

SetTimeout is a function in node: 
```
Rob@RobPC MINGW64 ~/Documents/coding/zeromasterywebdev/node (master)
$ node
Welcome to Node.js v12.16.3.
Type ".help" for more information.
> global.setTimeout
[Function: setTimeout] {
  [Symbol(nodejs.util.promisify.custom)]: [Function]
}
>
```
Can add it to script.js: 
```
const a =4;
const b=5;
setTimeout(()=> {
	console.log(a + b);
}, 3000)
```
Can get directory: 
```
console.log(__dirname);
```

