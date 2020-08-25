A REST API defines a set of functions which developers can perform requests and receive responses via HTTP protocol (e.g. GET, POST, PUT, DELETE).

REST APIs are stateless- meaning calls can be made indepedantly of one another. Each call contains all the data necessary to complete the call successfully. 

A GET request will have a request object that we receive. A request object can have a few things: 

### req.query ###
Add console.log(req.query) to standard GET request shwon before:

```
const express = require('express');
const app = express();

app.get('/', (req, res) =>{
	console.log(req.query);
	res.send("getting root");
});

app.listen(3000);
```
Then add the following as URL: 

http://localhost:3000/?name=Rob&age=45

Console will log: 

{ name: 'Rob', age: '45' }

### req.body ###

Used in previous lecture. This uses urlencoded or JSON body-parsers (middleware) to receive whatever the request sends to the body. 

### req.headers ###

Add this code: 
```
app.get('/', (req, res) =>{
	console.log(req.headers);
	res.send("getting root");
});
```
Then select headers in Postman and enter values into the input fields, when sent it will log header info and inputted data in terminal: 

```
{
  name: 'George',
  'content-type': 'application/json',
  'user-agent': 'PostmanRuntime/7.26.3',
  accept: '*/*',
  'postman-token': 'c47f1fbe-24fb-4743-a66e-5e017d13b461',
  host: 'localhost:3000',
  'accept-encoding': 'gzip, deflate, br',
  connection: 'keep-alive',
  'content-length': '48'
}
req.params

```

### req.params ###

Add this code: 
```
app.get('/:id', (req, res) =>{
	console.log(req.params);
	res.send("getting root");
});

app.listen(3000);
```

Syntax where you use the parameters of the URL. If add  the following in Postman and end GET request:

localhost:3000/1234

This will return the following in terminal: 

{ id: '1234' }

### res ###

Add code: 
```
app.get('/:id', (req, res) =>{
	console.log(req.params);
	res.status(404).send("not found");
});

app.listen(3000);
```

Then send in Postman. It returns 404 and not found in body in Postman. Then if refresh browser it shows 404 in network tab. 

### Serving static assets/files ?? ###

What if we want to serve things like styles.css, index.html.

Create folder called public with index.html. Then create HTML in file: 

```
<!DOCTYPE html>
<html>
<head>
	<title>hi</title>
</head>
<body>
 its working !!!
</body>
</html>

```

To get Express to send static files, add following code: 

```
const express = require('express');
const bodyParser = require('body-parser');
const app = express();

app.use(express.static(__dirname + '/Public'))

app.listen(3000);

```
This will return its working in browser. It network tab it has details. If did .css it would load it. 

