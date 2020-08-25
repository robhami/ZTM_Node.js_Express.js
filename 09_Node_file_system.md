FS stands for file system allows you to access our file system. Below imports fs module that comes with node. The FS module has a method -readfile(), that reads a file. First parameter is path to the file. 


```
const fs = require('fs');

fs.readfile('',(err,data) => {

  if(err) {
    console.log("error")
  }

  console.log(data);
  
})
