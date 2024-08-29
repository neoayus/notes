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