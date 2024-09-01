API stands for ***Application Programming Interface***. 
API basically is a URL. 
1. Web APIs 

APIs returns some data -----> in ***JSON*** format.

## Some Random APIs 
[Send random car facts](https://catfact.ninja/fact)   
[Send an Activity to do when bored](https://www.boredapi.com/api/acitivity)
[Send Cute Dog Pictures](https://www.boredapi.com/api/acitivity)

## JSON 
*Java Script Object Notation*. is a Data Format that contain `key` - `value` pairs. 
 [read about JSON @ json.org](www.json.org)  
 
**XML** was a thing before JSON. 

## Accessing Data from JSON 
### `JSON.parse(data)` Methos
to parse a String data into JS Object.
```
var randomcatfact= '{"fact":"neutering a male cat will, in almost all cases, stop him from spraying (territorial marking), fighting with other males (at least over females), as well as lengthen his life and improve its quality.","length":198}'; 

var understandableCatFact = JSON.parse(randomcatfact) ;
```
### `JSON.stringify(json)` Method 
to parse a JS object into JSON 



## Testing API requests
1. [Hoppscotch](hoppscoth.io) 
2. postman 
## Ajax / Ajaj 
Asynchronous JavaScript and XML . 
Asynchronous JavaScript and JSON . 

Sending a call to API is called Ajax Call. 

## HTTP Verbs

HTTP verbs, also known as HTTP methods, are the actions that clients can perform on a server's resources in a web application.
1. GET 
2. POST 
3. DELETE 
## Status Codes

HTTP status codes are standardized responses that a server sends to a client after receiving and processing an HTTP request. They indicate the outcome of the request and provide information about what happened on the server side. These codes are crucial in API development as they help clients understand whether their request was successful, if there was an error, and how to proceed.

1. 200  =>  OK 
2. 404  =>  NOT FOUND  
2. 400  =>  BAD REQUEST 
2. 500  =>  INTERNAL SERVER ERROR 

## Add Info. in URLs
### Query Strings

	https://ww.google.com/search?q=young+thug
key value pairs : 
	`q` -> key. (stands for query)
	`young thug` -> is value. 
	
 `:<variables>`  must be replaced with a valid value to access the API 
 

## HTTP Headers 

HTTP headers are key-value pairs sent between the client and server in an HTTP request or response. They carry essential information about the request or response, such as metadata, content type, cache settings, authentication details, and more. 

1. Request Headers. 
2. Response Headers. 

## API Request. 
using `fetch(url)` ;

