#event-handling #dom-events #dom #dom-events 
# DOM Events 
DOM Events are actions or occurrences that happen in the browser, which JavaScript can detect and respond to. Events can be triggered by user actions (like clicking a button, moving the mouse, or typing on the keyboard), or by the browser itself (like loading a page or finishing an animation).

#### Common Types of DOM Events:
##### Mouse Events:
1. click: Triggered when an element is clicked.  
		 `onclick = "" ; `
2. onmouseentere: Triggered when mouse in hovered on some button. 
3. dblclick: Triggered when an element is double-clicked.
4. mouseover: Triggered when the mouse pointer moves over an element.
5. mouseout: Triggered when the mouse pointer moves out of an element.
6. mousedown: Triggered when the mouse button is pressed down on an element.
7. mouseup: Triggered when the mouse button is released over an element.
8. mousemove: Triggered whenever the mouse pointer moves.
##### Keyboard Events:
***every key you press has a 'code' and 'key' value for it. 

1. keydown: Triggered when a key is pressed down.
2. keyup: Triggered when a key is released.
3. keypress: Triggered when a key is pressed and held down (deprecated, prefer using keydown).
##### Form Events:
1. submit: Triggered when a form is submitted.
2. focus: Triggered when an element (like an input) gains focus.
3. blur: Triggered when an element loses focus.
4. change: Triggered when the value of an input, select, or textarea is changed.
5. input: Triggered whenever the value of an input or textarea is modified.

## How to Handle DOM Events in JavaScript:
There are different ways to handle events in JavaScript. Here are the most common methods:
### 1. Inline Event Handler:
Directly in the HTML element using the onclick, onchange, etc., attributes. 
+ `onclick = "<js code> " ;` 
+ `onchange = "<js code> " ;`  
`<button onclick="alert('Button Clicked!')">Click Me</button>` 

### 2. Using JavaScript Properties:
By assigning an event handler directly to a property of a DOM object (e.g., onclick, onmouseover).

```
	const button = document.getElementById('myButton');
	button.onclick = function() {
		  alert('Button clicked using property!');
	};
```
### 3. Event Listener :  
Using the `addEventListener()` method, which is the recommended approach since it allows multiple event handlers and better separation of HTML and JavaScript.

***$ynt@x :*** 
```
<objectName>.addEventListener(<event>, <callback>) ; 
```

*there is a pre-defined parameter in 'callback' named `event` which holds lots of properties for that event.*
`object.addEventListener("eventName", function(event){ }`
> `event.preventdefault()` : this function allows to stop the actions that happens by default. 

**EXAMPLE HTML CODE:*** 
```
<!DOCTYPE html>
<html>
<head>
  <title>event listener example</title>
</head>
<body>
  <button id="myButton">Click Me</button>
</body>
</html>
```

**JS CODE:*** 
```
    // Select the button
    const button = document.getElementById('myButton');

    // Add a click event listener
    button.addEventListener('click', function() {
      alert('Button was clicked!');
    });
```

#### `this` in EventListener
When `this` is used in a callback of event handler of `something`, it refers to that `something` .

## `change` and `input` events ; 
The change and input events in JavaScript are used to detect changes in form elements, particularly input fields. Both events are essential for handling user input, but they behave differently and are used in different scenarios.

### 1. change Event
The change event is triggered when the user changes the value of an input element (e.g., `<input>, <textarea>, <select>)` and then moves away from that element (i.e., the element loses focus).
``

### 2. input Event
The input event is triggered every time the value of an input element changes, meaning it fires immediately as the user types, deletes, or modifies the content. It is more granular and fires continuously as the input value changes.

## Event Bubbling 
Event Bubbling is a mechanism in the DOM (Document Object Model) where an event propagates or "bubbles up" from the deepest (most specific) target element to the least specific ancestor element. When an event occurs on an element, it first triggers the handlers on that element itself, and then it propagates (bubbles) up to its parent elements, triggering their handlers, and continues this way up to the document object.

### `event.stopPropagation()` 
The `event.stopPropagation()` method is used to stop the event from propagating up the DOM tree. When called in an event handler, it prevents any parent elements from receiving the event.

```
document.getElementById("child").addEventListener("click", function (event) {
  console.log("Button Clicked");
  event.stopPropagation(); // Stops the event from bubbling up
});

document.getElementById("parent").addEventListener("click", function () {
  console.log("Parent Div Clicked");
});

```