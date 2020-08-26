FS stands for file system allows you to access our file system. Below imports fs module that comes with node. The FS module has a method -readfile(), that reads a file. First parameter is path to the file. Therefore need to create file call hello.txt in same folder and "hello" to it. Also need to do some encoding to console.log by adding .toString() to data. This will run utf8 encoding by default


```
const fs = require('fs');

fs.readFile('./hello.txt',(err,data) => {

  if(err) {
    console.log("error")
  }

  console.log(data.toString());
  
})

```

Above will return content of hello.txt to Terminal when you do (note do the same to call the code  to run in below examples: 

```
node script.js

```
### readFileSync ###
Sync stands for synchronous:

```
const file = fs.readFileSync('./hello.txt');
console.log('2',file.toString());
```

readFileSync will run first because its synchronous and readFile is asynchronous. readfile is asynchronous and thats why it has a callback function. It will reafile then run rest of code before executing callback function. Whereas fileSync does it straight away, this will be less efficient with alot of pauses to excute when alot of reading commands. 


### appendFile ###
The below will add text to existing file (and will create new file if one doesn't exist):

```
fs.appendFile('./hello.txt', ' This is so cool!', err =>{
 if(err){
 	console.log(err)
 }

})
```

Above will write to file then appear in terminal on next time it runs and then keep adding each time it runs. 

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

