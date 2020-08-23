3 types of modules: 

1. Modules you create yourself (e.g. ./script.js)

2. Built in modules:
```
const c =require('fs');

console.log(c);
```
This allows you to read file system.

initiate npm to get json file: 

```gitattributes
Rob@RobPC MINGW64 ~/Documents/coding/zeromasterywebdev/node (master)
$ npm init -y
```
then install nodemon: 

```gitattributes
Rob@RobPC MINGW64 ~/Documents/coding/zeromasterywebdev/node (master)
$ npm install nodemon --save-dev
```

The --save-dev puts the nomdemon in devDependencies in json file: 
```
{
  "name": "node",
  "version": "1.0.0",
  "main": "script.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "author": "",
  "license": "ISC",
  "keywords": [],
  "description": "",
  "devDependencies": {
    "nodemon": "^2.0.4"
  }
}
```
This just uses the nodemon whilst in developer mode. 

Nodemon is in the node_modules/.bin folder. So can do this in package.json file: 

```
 "scripts": {
    "start": "nodemon"
  },
  
```
then run:
```
Rob@RobPC MINGW64 ~/Documents/coding/zeromasterywebdev/node (master)
$ npm start

> node@1.0.0 start C:\Users\Rob.000\Documents\coding\zeromasterywebdev\node
> nodemon

[nodemon] 2.0.4
[nodemon] to restart at any time, enter `rs`
[nodemon] watching path(s): *.*
[nodemon] watching extensions: js,mjs,json
[nodemon] starting `node script.js`
361
C:\Users\Rob.000\Documents\coding\zeromasterywebdev\node
[nodemon] clean exit - waiting for changes before restart
[nodemon] restarting due to changes...
[nodemon] starting `node script.js`
362
C:\Users\Rob.000\Documents\coding\zeromasterywebdev\node
[nodemon] clean exit - waiting for changes before restart

```
no demon will listen for changes so recalculates result as 362 when change const b=6. So dont have to keep running nod script.js command. 
```

