## Node file system ##

### readFile ###
FS stands for file system allows you to access our file system. Below imports FS module that comes with Node. 

The FS module has a method -readfile(), that reads a file. First parameter is path to the file. Therefore need to create file call hello.txt in same folder and "hello" to it. Also need to do some encoding to console.log by adding .toString() to data. This will run utf8 encoding by default


```
const fs = require('fs');

fs.readFile('./hello.txt',(err,data) => {

  if(err) {
    console.log("error")
  }

  console.log(data.toString());
  
})

```

Above will return content of hello.txt to Terminal when you do: 

```
node script.js

```
(note do the same to call the code to run in below examples)

### readFileSync ###
Sync stands for synchronous:

```
const file = fs.readFileSync('./hello.txt');
console.log('2',file.toString());
```

readFileSync will run first because its synchronous and readFile is asynchronous. 

readfile is asynchronous and thats why it has a callback function. It will read file then run rest of code before executing callback function (e.g. err or date). 

Whereas readFileSync does it straight away. This will be less efficient as it will pause reading of code to execute readFileSync. Whereas readFile will wait till end before executing.  


### appendFile ###
The below will add text to existing file (and will create new file if one doesn't exist). 

First parameter is file to append, second - what we want to add, third is for an error response:

```
fs.appendFile('./hello.txt', ' This is so cool!', err =>{
 if(err){
 	console.log(err)
 }

})
```

Above will append 'This is cool!' to the text in hello.txt. Appended text then appear in terminal on next time it runs and then keep adding each time it runs. 

### writeFile ###

The below will create new file and add text to it: 

```

fs.writeFile('bye.txt','sad to see you go', err =>{
 if(err){
 	console.log(err)
 }

})
```
### DELETE unlink ###
This will delete file: 

```
fs.unlink('./bye.txt', err =>{
 if(err){
 	console.log(err)
 }
console.log('bye gone')
```

})

### Santas helper challenge ###

Use console.time, to see how long each call takes. Need a console.timeEnd with same value in brackets as console.time to track time between two console entries.  

e.g. 

```
const fs = require('fs');
fs.readFile('./hello.txt',(err,data) => {
  console.time('time taken');
  if(err) {
    console.log("error")
  }
  console.timeEnd('time taken');
  console.log(data.toString());
  
})	

```
