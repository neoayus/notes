1. JS is **Case Sensitive**.
2. **Semi colon** `;` is required to end statements just like other programming languages. 
3. **Comments**  : 
	1. Single Line Comments : `//` *this is your comment*  
	2. Muti-Line Comment : ``` /* this is a mutiple line commment.  ```
4.  JS is **Dynamically Typed** language. 
5. ***`Nan`*** is a global property rep. 'Not a Number' .
6.  Everything in JS has `Truth` and `False` values in Boolean context. 
7. `const`   keyword is used to make constant vars. 
8.  `this` keyword is refers to an object that is executing the current piece of code. also, used as object name insider object function. 
9. 
## How to assign variables?
`let` and `var` keywords are used in JS to assign variables 
example: 
```
let x = 10 ; 
var my_variable ; 
```
## Datatypes in JS 

### Primitive Datatypes: 
1. Boolean : JS boolean only true values either `true` or `false` . 
2. Undefined : a var has undefined value when no value is assigned to it. 
			`var my_variable; `
3. String : textual content enclosed in single or double inverted coommas. 
			`var myString = "surprise mf" ; `
4.  Null : 'null' simply means ***absence of value.*** 
5. Number : numbers can rep 'integer', 'float', 'hexadecimal', 'octal' or 'exponential' values. 
### User Defined Datatypes: 
1. OBJECT : objects hold multiple values in terms of *properties* and *methods.* 

## Functions/Methtods

this is how you define functions in JS. 
```
this-is-an-function(){
	var random-task = "I can do random task for you" ; 
	return random-task ; 
}
```
### Method Chaining
2 or more methods can be chained together like: 
`str.toUpperCase().trim()` : will remove the trailing white spaces and change the string to UPPERcase.

### Function Expressions: 
Substitute for defining a function for **Nameless functions whose values gets stored in a n variables** 
```
const sum = function(a,b){
	return a+b ; 
}
```
### Higher Order Functions: 
functions who : 
1. take one or multiple functions as arguments. 
2. returns a function. 

### String Methods
1. `<string>.trim()` : trims whitespaces
2.  `<string>.toUpperCase()` and `<string>.toLowerCase`
3. `<string>.indexOf('arg')` : returns the first index of occurace of `arg` in string. 
4. `<string>.slice(INDEX)` : returns a part of original String
			`<string>.slice(starting_index, end_index)` 
			`<string>.slice(num)` = `str.slice(length-num)`
5.  `<string>.replace('search', 'replace')` :  replaces strings w the first one, 
6. `<string>.repeat('x')` : repeat string 'x' times. 
7. 

### Array Methods
1. `indexOf()` :    returns index of a value. 
2. `includes("")` :    search for an values. 
3.  `.concat(array1, array2)` :  merge 2 arrays. 
4. `.reverse` :    reverse an array. 
5. `.slice()` :    copies a portion of array  
		`.slice(index)` / `.slice(start, end)` where start in inclusive and y is exclusive. 
6. `.splice()` :     reverse/replaces/add elements in place. 
	  `.splice(start, deleteCount, intem0...item1)` 
7.  `.sort()`  :    to sort an array  


### [[PRE-DEFINED FUNCTIONS IN JS]] 
these are functions pre defined in js

## Naming Conventions

There are mainly 3 naming conventions. 

- ***thisIsCamelCase***
- ***ThisIsPascalCase***
- ***this_is_snake_case*** 

## Switch Statement

The `switch` statement in JavaScript is used to perform different actions based on different conditions. It's an alternative to using multiple if...else if...else statements when you want to compare a single expression against multiple possible values. 

```
switch (expression) {
  case value1:
    // Code to execute if expression === value1
    break;
  case value2:
    // Code to execute if expression === value2
    break;
  // Add more cases as needed
  default:
    // Code to execute if none of the cases match
}
```
## LOOPS 
### `for` loop : 
The `for` loop is the most commonly used loop in JavaScript. It repeats a block of code a specific number of times.
```
for (initialization; condition; increment) {
    // Code to be executed
}
```

### `while` loop : 

The `while` loop repeats a block of code as long as a specified condition is true.

```
while (condition) {
    // Code to be executed
}
```
### `do...while` loop : 

The `do...while` loop is similar to the while loop, but it checks the condition after executing the code block, ensuring that the loop runs at least once.

```
do {
    // Code to be executed
} while (condition);
```

### `for...in` loop : 

The `for...in` loop iterates over the properties of an object (or the indices of an array).

```
for (key in object) {
    // Code to be executed
}
```

## Arrays 
 Array is a data structure that allows you to store multiple values in a single variable. Arrays can hold any type of data, including numbers, strings, objects, and even other arrays.
 There are several ways to create arrays in JavaScript.  
### 1. Using Square Brackets (Array Literal) : 
```
let fruits = ["Apple", "Banana", "Mango"];
```
### 2. Using the Array Constructor : 
```
let fruits = new Array("Apple", "Banana", "Mango") ; 
```
## Objects 

 `ojects` are one of the fundamental data structures used to store collections of data and more complex entities. An object is a collection of properties, where each property is defined as a 
 `key-value` pair.
```
let person = {
    name: "John",
    age: 30,
    city: "New York"
};
```
#object 
### Accessing Object Properties
You can access the properties of an object using either dot notation or bracket notation.
1.  Dot Notation 
```
	console.log(person.name); // Output: John
```
2. Bracket Notation
```
	console.log(person["age"]); // Output: 30
```

### Deleting Properties
we user `delete` keyword to delete key's. 
```
	delete person.city;
	console.log(person.city); // Output: undefined
```

### Methods in Objects
A method is a function that is a property of an object. 
```
let person = {
    name: "John",
    age: 30,
    greet: function() {
        console.log("Hello, my name is " + this.name);
    }
};

person.greet(); // Output: Hello, my name is John
```


## String. 
### String Interpolation 

String interpolation allows you to embed expressions directly inside a string.

- The `${}` syntax is used within a template literal to insert the value of a JavaScript expression (like variables, calculations, or function calls) into the string.

- Everything inside `${}` is evaluated as JavaScript code, and the result is automatically converted to a string and inserted into the surrounding text.

```
let name = 'neoayus';
let age = 20;
let greeting = `Hello, ${name}! You are ${age} years old.`; // Using string interpolation
console.log(greeting); // Output: Hello, Memphis! You are 21 years old.
```


## Scope : accessibility of variables. 
Objects and methods can be accessed from different part of code. 
### 1. Function 
Variables declared inside f() can be accessed inside functions only. 
### 2. Block  `{}` 
Variables declared inside a block can't  be accessed outside the block. 
### 3. Lexical 
variable defined outside the function can be accessible inside another function defined after the variable declaration. 
```
{
	outer{
		let a = 5 ;
		function inner(){
			:/code 	
		}	
	}
}
```
### 4. Global 
Variables with Global scope. 

## try & catch 

`try` statement allows us to define a block of code to be tested for errors and, 
`catch` statement allows you to define a block of code to be executed if an error occurs in `try` block. 
```
try{
	//	
}catch{
	//
}
```
***console.log(err)*** : **console log the error, (used insider catch).** 


