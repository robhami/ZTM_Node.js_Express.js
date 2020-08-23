
### Install Express ###
```
Rob@RobPC MINGW64 ~/Documents/coding/zeromasterywebdev/node (master)
$ npm install express
```
Add code to server.js file (delete old HTTP stuff): 
```
const express = require('express');

const app = express();

app.listen(3000);
```
This just returns "cannot / GET" in browser. To send something:

```
const express = require('express');

const app = express();

app.get('/', (req, res) =>{
	res.send("hello");
});

app.listen(3000);
```
Express can automatically convert/stringify to JSON: 
```
const express = require('express');

const app = express();

app.get('/', (req, res) =>{
	const user = {
		name: 'Sally',
		hobby: 'soccer'
	}
	res.send(user);

});

app.listen(3000);
```
By changing url will get different responses:
```
const express = require('express');

const app = express();

app.get('/', (req, res) =>{
	res.send("getting root");
});
app.get('/profile', (req, res) =>{
	res.send("getting profile");
});
app.get('/profile/obj', (req, res) =>{
	const user = {
		name: 'Sally',
		hobby: 'soccer'
	}
	res.send(user);

});

app.listen(3000);
```
e.g. localhost: 3000/ will give "getting root"
localhost: 3000/profile will give "getting profile"
localhost: 3000/profile/obj will give user object

Can use get, post, delete and push method.




