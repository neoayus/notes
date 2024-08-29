#java_script #js #dom 
*** > : represents a console command in my notes. 

`> console.log(document)` : to access html looking code. 

`> cosole.dir(documents);` : access properties and functions of documents. 

### to change an element in html and css 

+ select an element. 
+ Update it. 

## Selecting Elements 

+ You can access these elements and store them in some variables. 
	+ then use `console.dir(thatVaraible) ;`  to access the properties of given variable. 
	+ and `console.log(<variable>) ; ` to show that variable in console log. 
	
	+ variable's properties area accessible and we can also print them. 
			+ `objectName/variableName.<property>`
### 1.  getElementById 

used to access elements using the id given to them. 

`document.getElementById("your_id")`

### 2. getElementsByClassName

Returns the elementS(collection) as HTML Collection or empty collection(if not found)  ; 

`document.getElementsByClassName("class_name"); `

as classes can have multiple elements, we can access them using indexes.
`document.getElementsByClassName(<class_name>)[<index>] ; `
`document.getElementsByClassName(<class_name>)[<index>].<property> ; `

### 3.  getElementsByTagName 

Returns the elementS(collection) as HTML Collection or empty collection(if not found)  ; 

`document.getElementByTagName("<tagName>") ; `  
### 4.  querySelector 

This selector allows us to use any element using css selector and is **only used to select a Single Element.**  

for example : 
1. to access a element using class, we can use `document.querySelector(".className") ; `
2. to access a element using id, we can use `document.querySelector("#idName");` 
3. to access a element using element name, we can use `document.querySelector("<element>");` 

to select all the element : 
`document.querySelectorAll("<element");` is used. 

NOTE : We Can Also Select Pseudo Elements here. 

## Content Manipulation in  Objects  

Updating Values in node using selected elements. 
```
var <node> = document.querySelector("p"); 
node.<property> = <value>  ; 
```

### 1: Content Manipulation  

***InnerText*** : Shows the visible text contained in a node. 
***textContent*** : Shows all the full text.  
***InnerHTML*** : Shows the full markup. 

*leme show y'all something cool :* 
```
var head = document.querySelector(".heading") ; 
head.innerHTML = `<u>${head.innerText}</u>`
```
*this code will take the value from .heading class's text and add underline to it to update the head.innerHTML*

### 2.  Attribute Manipulation 

Attributes in html are : Id, Class, Style and everything else except `<element>` ;

> Store the Object in some variable using GETTER and set it's value using SETTER . 
#### Get Attribute. 
`<obj>.getAttribute(<attribute>) ;`	
#### Set Attribute. 
`<obj>.setAttribute(<attribute>,<value>) ;`	

### 3.  Style Manipulation 

to check style(CSS) of an object :  `<object>.style`

LIMITATION : we can only access inline css

***we turn KEBAB CASE to CAMEL CASE in JS*** 
`background-color: red ; ` will be `backgroundColor : red `

#### to modify css : 
`<object>.style.<property> = <value>` 

#### Using  ClassList. 

 to check all the classes in of  an object, we use :  `<object>.classList`

`classList.add()` : to add new classes 
`classList.remove()` : to add remove classes 
`classList.contains()` : to check if class exists 
`classList.toogle()` : to toggle between add and remove (creates a class if it dosen't exist and delete if it does) 

we prefer CLASSLIST > SET ATTRIBUTE because, set att. only allows 1 class to be working on objects. 


## Navigation on Page.

to move between element in Document. 

1. parentElement  : 
		 '`<object>.parentElement`
		 
3. children :
	1. `<object>.children` : to print all the children of element. 
	2. `<object>.childElementCount` : to print all the children of element. 
		 `<object>.parentElement` && `<object>.parentElement[0]`
		 children can be multiple so we can add index in. 
		 
4. previousElementSibling / nextElementSibling  : 
		 `<object>.previousElementSibling` 
		 `<object>.nextElementSibling` 

## Adding Elements 

`document.createElement(<element>)`  : is used to create new elements in documents
and to insert elements in webpage. 

1.  `<object>.appedChild(element)` :   append the element as child to the current object 
2.  `<object>.append(element)` :   append element to the current object. 
3.  `<object>.preped(element)` :   append element before the current objecrt. 
4. `<object>.insertAdjacent(where,element)` : 
## Removing Elements 
to remove elements from document. 

1. `<object>.removeChild(<element>)` : to remove the child element of the object. 
2. `<object>.remove()`  :   to remove the object itself. 

>> CONTINUING THE REST OF DOM IN : 
>>> [[Event Handling in JS using DOM Events]]
>>> 