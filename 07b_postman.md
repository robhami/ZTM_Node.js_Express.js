### Install Postman ###

Go to: 
https://www.postman.com/

### GET request Postman from code ###

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

![Alt Text](https://github.com/robhami/ZTM_Node.js_Express.js/blob/master/images/postman_get.PNG)

### POST request Postman from code ###
Enter localhost:3000/profile into Postman and do a POST request. This returns send value user values to body lower pane i.e.:
![Alt Text](https://github.com/robhami/ZTM_Node.js_Express.js/blob/master/images/postman_post_first.PNG)


Can select options by clicking on body in upper pane:  
1. form-data
2. x-www.form-urlencoded
3. raw
4. binary

You will use data type #2 above if use a server for a form that gets submitted in HTML.

If add a Key and value (did this under #2 above) req.body doesnt do anything when you POST because you need middleware- it only gives undefined in terminal. 
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
urlencoded is added as this is the data selected in Postman (see #2 above).
```
app.use(bodyParser.urlencoded({extended: false}))
```
Also need to pass it a parameter: {extended: false}. There is a link that explain more on this:

ADD LINK 

### POST request Postman from Postman body ###

#### urlencoded ####

Go to Postman and do Post 

![Alt Text](https://github.com/robhami/ZTM_Node.js_Express.js/blob/master/images/postman_post.PNG)

This will return entered values in console:
```
[Object: null prototype] { name: 'Rob' }
```

#### JSON ####

There is also JSON under Raw. 

Need to add line of code to tell bodyParser to accept JSON:
```
app.use(bodyParser.urlencoded({extended: false}))
** app.use(bodyParser.json()); **

```
Enter new user into upper pane of Postman:
![Alt Text](https://github.com/robhami/ZTM_Node.js_Express.js/blob/master/images/postman_post_JSON.PNG)


This will return the following in console: 
```
{ user: 'Jenny', hobby: 'tennis' }
```

So we could add the user to database (then call it with req.body - below its just console.logged from the Postman body of /profile). Then send success message to lower body  
```
app.post('/profile', (req, res) =>{
	console.log(req.body);
	res.send('Success');
});
```
This returns a Success message in lower pane of Postman. 
![Alt Text](https://github.com/robhami/ZTM_Node.js_Express.js/blob/master/images/success.PNG)

### PUT ###
Can use PUT to update e.g. if you want Jenny to have a different hobby

### DELETE ###
If you want to delete user. 
