
## Middleware ##
Request passes through the Middleware code then onto next bit of code. Middleware can do something to code to perhaps make it easier to work with. 
app.use gets request but does not move to next response on until next is used, if next is ommitted it just stops and only sends hello to terminal and not testest to browser

```
const express = require('express');

const app = express();

app.use((req, res, next) => {
  consol.log('<h1>Hello</h1>')
  next();
})


app.get('/', (req, res) =>{
	res.send("testtest");
});

app.listen(3000);
```

This called middleware.
