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