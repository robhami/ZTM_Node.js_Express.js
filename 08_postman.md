Go to: 
https://www.postman.com/

Can add get request to where we have server running from Postman. 

NPM start the following code/server:

```
const express = require('express');

const app = express();

app.get('/', (req, res) =>{
	res.send("getting root");
});
app.get('/profile', (req, res) =>{
	res.send("getting profile");
});
app.post('/profile/obj', (req, res) =>{
console.log(req.body);
	const user = {
		name: 'Sally',
		hobby: 'soccer'
	}
	res.send(user);

});

app.listen(3000);
```

Then enter localhost:3000/profile into Postman and do a GET request. This returns send value- "getting profile". 

### POST ###

can select options by clicking on body:  
1. form-data
2. x-www.form-urlencoded
3. raw
4. binary

If add a Key and value req.body doesnt do anything because you need middleware-it only gives undefined in terminal. 

### Body-Parser ###

npm install body-parser

npm start

add following code to above:
```
const express = require('express');
** const bodyParser = require('body-parser'); **
const app = express();

app.use(bodyParser.urlencoded({extended: false}))


app.get('/', (req, res) =>{
	res.send("getting root");
});
app.get('/profile', (req, res) =>{
	res.send("getting profile");
});
app.post('/profile', (req, res) =>{
	console.log(req.body);
	const user ={

		name: 'Sally',
		hobby: 'soccer'

	}



	res.send(user);

});

app.listen(3000);
