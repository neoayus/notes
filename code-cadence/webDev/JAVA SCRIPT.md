## Linking JS Files in HTML. 

##### This is How to link  External JS files in Html:

JS is preferred to be linked in last of `<body>` tag cause  If you place the `<script>` tag in the `<head>`, the script will load before the body content is rendered. This may delay the page rendering.  
```
<html>
<head>
    <title>My Web Page</title>
</head>
<body>
 <!-- Your HTML Content Goes her --> 
 <!-- Link to the JavaScript file -->
    <script src="script.js"></script>
</body>
</html>
```

##### Writing JS code inside `<script>` Tag. 
You can also include JavaScript directly within the HTML document using the `<script>` tag:
```
<html>
<head>
    <title>My Web Page</title>
</head>
<body>
    <!-- Your HTML content goes here -->

    <!-- Inline JavaScript -->
    <script>
        console.log("Hello, World!");
    </script>
</body>
</html>
```

## Java Script  Basics.  
I already know the basics of Java Script already. 
anyways i have linked, [[basic js]] for times i need a Quick Revision. 

## Useful Predefined Functions\
there are some [[PRE-DEFINED FUNCTIONS IN JS]] that we ofenly use, and you should know about.  


# Objects  : 
i already know the basics of  #object in [[JAVA SCRIPT]] . 
>I'll just add new and important info. here.   

##### Default JS Object
1. `window` :   
2. `Document` : is used for [[DOM (document object manipulation)]] . 

# DOM : 
[[DOM (document object manipulation)]] is a programming interface for web documents. It represents the structure of an HTML or XML document as a tree of objects, where each node corresponds to a part of the document, such as an element, attribute, or text.

The DOM allows JavaScript (or other languages) to access and manipulate the content, structure, and style of web pages dynamically.

### Key Features of the DOM:

***1.  Tree Structure:*** The DOM represents the document as a tree structure. The root node is the document, and every element (like `<body>, <div>`, etc.) becomes a branch or leaf.   

***2. Node Types :***  Each part of the document is a node in the DOM. The most common types are:
1. **Element Node:** Represents an HTML element like `<p>, <div>, <img>.`
2. **Text Node:** Represents the text inside an element.
3. **Attribute Node:** Represents the attributes of an HTML element (like id, class, etc.).

***3. Manipulation:*** The DOM provides a variety of methods to manipulate the document:

***4. Event Handling:*** The DOM allows JavaScript to listen to and respond to user actions, like clicks, key presses, and mouse movements, through event listeners e.g. `addEventListener()

>> Detailed note on [[Event Handling in JS using DOM Events]]... 

