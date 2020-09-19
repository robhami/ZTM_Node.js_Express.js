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
Enter localhost:3000/profile into Postman and do a POST request. This returns send value user values to body i.e.:
```
{
	name: 'Sally',
	hobby: 'soccer'
	}.
```	

Can select options by clicking on body:  
1. form-data
2. x-www.form-urlencoded
3. raw
4. binary

You will use data type #2 above if use a server for a form that gets submitted.

If add a Key and value (did this under #2 above) req.body doesnt do anything because you need middleware-it only gives undefined in terminal. 
If you want to access req.body you need to use middleware called:

#### Body-Parser ####

npm install body-parser

npm start

add following code to above:
```
const express = require('express');
** const bodyParser = require('body-parser'); **
const app = express();

** app.use(bodyParser.urlencoded({extended: false})) **


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
```
 Also this is why urlencoded is added to:
```
app.use(bodyParser.urlencoded({extended: false}))
```
Also need to pass it a parameter: {extended: false}. There is a link that explain more on this:

ADD LINK 

Go to Postman and do Post 







There is also JSON under Raw. 
Need to add line of code to tell bodyParser to accept JSON:
```
app.use(bodyParser.urlencoded({extended: false}))
** app.use(bodyParser.json()); **

```
Can also send success message: 
```
app.post('/profile', (req, res) =>{
	console.log(req.body);
	res.send('Success');
	const user ={

		name: 'Sally',
		hobby: 'soccer'
	}

	res.send(user);

});
```