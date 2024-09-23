CSS Stands for ***cascading style sheet***  and is used to **style**  webpages. 

### There are 3 ways to write CSS in a webpage. 

1. Inline : `style` attribute is used inside a tag. 
		`<p style = "color: white; background-color: black;"`  
		
2. Internal CSS : `<style> </style>`  is used inside `<head>` tag. 
```<head>
<title>Style Tag</title>
<style>
h4{
color : aqua ; 
}
div{
background-color: black;
}
</style>
</head>
```
3. External CSS : creating another `filename.css` file and pasting all the CSS code there. and link it in `<head>` tag using `<link>` tag, like: 

```<link rel="stylesheet" href="3-css4external_styleSheet.css">```

## new FLEX properties ;

+ `order` : Sometimes reversing the row or column order of a container is not enough. In these cases, we can apply the order property to individual items. By default, items have a value of 0, but we can use this property to also set it to a positive or negative integer value (-2, -1, 0, 1, 2).

+ `align-self` : to align item itself. 

+ `flex-wrap` : specifies whether flex items are forced on a single line or can be wrapped on multiple lines.

+ `flex-flow` : Shorthand property for flex-direction and flex-wrap.

