Create server.js file: 
```
Rob@RobPC MINGW64 ~/Documents/coding/zeromasterywebdev/node (master)
$ touch server.js
```
Change JSON to access this file: 
```
 "scripts": {
    "start": "nodemon server.js"
  },
```
Add the following to server.js. http is a built in module that will import/require then create server that uses arrow function on http. Then listen to server on port 3000.
```
const http = require ('http');

const server = http.createServer(()=> {
	console.log("I hear you! Thanks for the request.")
})


server.listen(3000); 
```
 Go to localhost:3000 in browser. Then run server.js: 
 ```
 Rob@RobPC MINGW64 ~/Documents/coding/zeromasterywebdev/node (master)
$ node server.js
I hear you! Thanks for the request.
```
Will message/console.log in terminal everytime refresh localhost, however browser just hangs at moment because not sending anything. To do that: 
```
const http = require ('http');

const server = http.createServer((request, response)=> {
	response.setHeader('Content-Type', 'text/html');
		response.end('<h1>Helllo</h1>');
})


server.listen(3000); 
```
Any time we try to connect we have a  request and response parameter we can use. 

Above will show hello in browser when you run server.js.

Can also get information about the request: 
```
const http = require ('http');

const server = http.createServer((request, response)=> {
	console.log('headers', request.headers);
	console.log('method', request.method);
	console.log('url', request.url);
	
	response.setHeader('Content-Type', 'text/html');
	response.end('<h1>Helllo</h1>');
})


server.listen(3000); 
```
This gives info about requests: 
```
headers {
  host: 'localhost:3000',
  connection: 'keep-alive',
  'cache-control': 'max-age=0',
  'upgrade-insecure-requests': '1',
  'user-agent': 'Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/84.0.4147.135 Safari/537.36',
  accept: 'text/html,application/xhtml+xml,application/xml;q=0.9,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.9',
  'sec-fetch-site': 'none',
  'sec-fetch-mode': 'navigate',
  'sec-fetch-user': '?1',
  'sec-fetch-dest': 'document',
  'accept-encoding': 'gzip, deflate, br',
  'accept-language': 'en-GB,en-US;q=0.9,en;q=0.8,la;q=0.7'
}
method GET
url /
```
If add text to url, it will return that text:
```
http://localhost:3000/profile123

url /profile123

```

To send JSON response creatye object and use JSON.stringify:
```
const http = require ('http');

const server = http.createServer((request, response)=> {

	const user = {
		name: 'John',
		hobby: 'Skating'

	}
	
	response.setHeader('Content-Type', 'application/json');
	response.end(JSON.stringify(user));
})


server.listen(3000);
```
Will run json.parse() on front-end to convert it to a JS object.

Better to use express.js with node.js.
