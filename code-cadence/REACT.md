react is a JS library for UI
react is used to write Individual re-usable pieces of code called **components**.
component = html + css + js.  #html #css #jss #react 
# JSX
stand for ***JavaScript Extension Syntax*** 
which allows html to be written inside of js. 

JSX --> babel --> JS 

#JsTips
+ anything within curly braces `{}` is treated as pure JS. 
+ everything is build in hierarchy 
+ no's to be passed inside {} in argument. 
# Setting Up Local Environment. 
1. Create a vite project. 
		`npm create vite@latest`
2. Name the project. 
3. Select Libraries. **React > JS**. 
4. Install Node Modules in the project folder. 
		`npm install`
5. START THE SERVER : 
	   `npm run dev`
# Re-Writing App
inside ***App.jsx*** 
```
import "./App.css"
function  App(){


	return(
	
	)
}

export default App 
```

# Component 
Individual re-usable pieces of codes in react are called **components**.
## creating an component . 
```
function <compnent name>(){
	return(
		<h1> This is the Title </h1> 
	); 
}
```
+ return values should only contain one parent element. 
## Rendering a component 
To render a component, we write it as an element. 
`<Title> </Title>`  or  `<Title/>`

>> ***we create different file for different components by the their name and  `.jsx` extension*** 
+ export that in the `componentName.jsx` and 
+ import in `App.jsx` 
### IMPORT 
`import <component name> from "<file path>"` ;
### EXPORT 
`export default <file name>` 
### NAMED EXPORT
`import {<component file name} from "<path>";` 
`export {<component file name};` 
FOR MULTIPLE FILES : `export {<component file name>, <second component file>};` 

# Writing Markup in JSX
1. return a single root element. 
2. use camelCase most of the times. 
3. Close all the tags. 

`<div> </div>` 
				OR
```
<div 
	<p> para </p>
	<h1> this is a heading </h1> 
/>
```
>tip :  we use `classname` instead of `class` as attribute in react. 

# react fragment
fragment lets you group a list of children without adding extra nodes to the dom. 
and empty tag is used to group things together wo creating a node in DOM. 
```
	<> 
		//HTML Elements Here!
	</>
```
# Styling in CSS. 
to style components in CSS, we write different stylesheets for every file. 
and import CSS directly in Component File.
	`import "<path to css file>" ; `

# React Props
Props are the info you pass to a JSX tag. 
	`<Product title="phone" price = "30k" /> `
default values can also be assigned to props just like function arguments. 

```
export default function Product({<firstProp>},{<secondProp>}){
	return(
		<div className = "Product"> 	
			<h4 {<firstProp>} />
			<p {price} /> 
	)
}
```

## Passing Arrays in Props 
array are first declared and then their variable is passed inside `{}` or directly too by using [] inside {}. 
and to pass OBJECTS directly, we use {} inside {} . 

***and for OBJECTs we use `objectName.keyValue` to access Object values in DOM*** 
## Passing Arrays Items in Props 
we embed the array items into `<pre/>` or `<li/>`.
OR
use `map` function to embed everything in list or paragraph. 

# Conditionals 
Adding element based on some conditions. 
`{ price >= 10000 ? <p Discount : 5% /> : null }`
or 
```
if (condition){
	// elements
}else{ 
	// elements
}
```

# Dynamic Component Styling
we can pass CSS to to an attribute named `style`  like `style = "<css here>"` 

1. create an variable 
`let css = {backgroundColor : "yellow"} ; `
2. pass that variable in `style` attribute.  
```
return(
	<div className = "division" style = "css">
		<h3>Titile </h3>  
		<h5>Price </h5>  
	</div>	
)
```

We can use that attribute to assign CSS to elements for certain Conditions by using Conditional Operators with them . 
`let css = {backgroundColor : price > 30000 ? "yellow" : ""} ; `

# EVENTS in react 
ON CLICK EVENTS :  an attribute named `onClick = {}` is added to the element you want to add even listener on.
for other events there are attributes like : `onMouseOver` and `onDoubleClick`

## EVENT Object
we can access the event object in Handler. 
```
function doSomething(event){
	event.preventDefault() ; // 
    console.log("did something!") ; 
    console.log(event) ; 
}

export default function Button(){
    return(
        <div>
            <button onClick={doSomething}> Click Me! </button>
        </div>
    );
}
```
# STATEs
The State is a built-in React object that is used to contain data or information about the component. A component's state can change over time; whenever it changes, the component re-renders. 

## Hooks
They let you use State and other React features without writing a Class. 

### `useState()`;
is a React Hook that lets you add a state variable to your component. 

and we have to **import use state from "react"** 
`import {useState} from "react" ;`

we'll deconstruct an array and create a state variable : 
`[<state variable>, <f() to set state variable>] = useState(<initial value> ;`
for example: 
			`let [count, setCount] = useState[0] ; `

```
import { useState } from "react" ; 

export default function Counter(){

    let [count, stateCount] = useState(0) ; // for usee state varibale, we can also use a function there.. 
    let incCount = ()  => { 
        stateCount(count + 1) ; 
    }    
    return(
        <div>
            <h3>Count = {count} </h3>
            <button onClick={incCount}>Increase Count</button>
        </div>
    );
}
```

## Callback in set state () 
set state is asynchronus functions so we can provide callbacks in it  to make it work as expected. 
```
export default function counter() {
	let[count, setCount] = setCount(0) ; 

	let incCount = () => {
		setCount((currCount) => {
			return currCount + 1 ; 	
		})	
		setCount((currCount) => {
			return currCount + 1 ; 	
		})	
	}; 

	return (
		<div> 
			<h2 Count = {count} onClick={incCount} />
		</div>
	) ; 
}
```

## Object and States / Arrays
In React, when you set an object (or an array) as a state variable, React uses shallow comparison to determine if the state has changed. A shallow comparison checks if the reference to the object (or array) has changed, not the contents of the object or array itself.

### Shallow Comparison and State Updates
1. Object/Array Reference: When you set an object or array as a state variable, React keeps track of the reference (the memory address) to that object or array.

2. 2. State Update without Change in Reference:

+ If you update a property of the object or an element of the array without changing the reference (i.e., without creating a new object/array), React won't detect the change.
+ This is because the reference (address) in memory remains the same, so React's shallow comparison assumes nothing has changed and therefore doesn't trigger a re-render.

**Example :**
```
import { useState } from "react" ; 

export default function LudoBoard(){
 //either
    // let [blueMove, setBlueMove] = useState(0) ; 
    // let [redMove, setRedMove] = useState(0) ; 
 // or 
    var[moves, setMoves] = useState({blue: 0, red: 0}); 
    var[count, setCount] = useState(0) ; 

 // f() to update blue values and using callBack values. 
    function updateBlue(){
        setMoves((preMoves)=>{
            return {...preMoves, blue : preMoves.blue+1} ;          
        });        
    };

    function updateRed(){
        setMoves((preMoves)=>{
            return {...preMoves, red : preMoves.red+1} ;          
        });        
    };
	
    return(
        <div>
            <h1>Game Begins!</h1>
            <div className="board">

                <p>Blue Moves = {moves.blue} </p>
                <button style={{backgroundColor : "blue"}} onClick={updateBlue}> +1</button>

                <p>Red Moves =  {moves.red} </p>
                <button style={{backgroundColor : "red"}} onClick={updateRed} >+1</button>
            
            </div>
        </div>
    );
}

```
# Closure
A closure is a feature in JS where an inner function has access to the outer (enclosing) function's variables. 
```
function outer(){
	var b = 10 ; 
	function inner(){
		vat a = 20 ; 
		console.log(a+b) ;	
	}
	return inner ; 
}

let inner = outer() ; 
console.log(inner); 
```

