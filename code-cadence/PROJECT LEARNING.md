#html #css #project
# **Including Fonts (CSS)**
[]
```cs
@font-face{
	font-family : Inter ;
	src: url(../directory) ;
}
body{
	font-family: Inter ;
}
```
# Black Overlay on a Image in the Same div. 
```
same_div{
	 //rest of css
	 
	&::before{
		content: '' ; 
		top: 0 ; 
		left: 0 ; 	
		 
		color: rgb(0,0,0,0.6) ; 
		position: absolute ; 
		z-index: 0 ; 
	}	
}

```
# Playing around withe the ::before pseudo element. 

#### GOAL : is to set the content in properties to be shown in background rather than on top as overlay. 
#### HTML : 
```
<!-- text area with some texts in it  -->
         <div class="st-container">
            <div class="container-heading">
               Live Sports 
            </div>
            <div class="container-text">
               Catch your games at home or on the go. Stream live games <br> from major college and pro leagues including the NCAA®, NBA, <br> NHL, NFL, and more.
            </div>
            
            <div class="icons">
               <div class="w-circ one")"></div>
               <div class="w-circ two"></div>
               <div class="w-circ three"></div>
               <div class="w-circ four"></div>
               <div class="w-circ five"></div>
            </div>
         </div>
```
#### CSS : 
```
/* CSS FOR ALL THE CIRCLES  */
.sportstv .content .st-container .icons .w-circ{
   /* height: 55px ; 
   width : 55px ; 
   
   background-color: pink;
   border-radius: 50% ; 
   margin: 23px 17px 0 0 ; 
   
   &::before{
      content : '' ; 
      top: 0 ; 
      left: 0 ; 
      height: 100% ;
      width : 100%; 
      background-color: white; 
      position : absolute ; 
      z-index: 1; 
      background-size: contain ; 
      background-repeat: no-repeat ; 
      background-position: center;
   }    */
 /* CHANGING THE CSS FOREVER  */
   height: 55px ; 
   width : 55px ; 
      background-size: contain ; 
      background-repeat: no-repeat ; 
      background-position: center;
   border-radius: 50% ; 
   margin: 23px 17px 0 0 ; 
   position: relative ; 

 /* setting background to be white for all the divs */
 /* doing this allows me to set the bg:white for all the divs and i have to change the circle in all the imageas only.  */
   content: '' ; 
   top: 0 ; 
   left: 0 ; 
   height: 55px ; 
   width: 55px; 
   background-color : white; 
   position : relative ;
   z-index: 1 ; 
   border-radius: 50% ; 
}

/* changing image in every circle  */

.st-container .icons .w-circ.one{
      background-image: url('./assets/47_original.png');
}
.st-container .icons .w-circ.two{
      background-image: url('./assets/65_original.png');
}
.st-container .icons .w-circ.three{
      background-image: url('./assets/57_original.png');
}
.st-container .icons .w-circ.four{
      background-image: url('./assets/49_original.png');
}
.st-container .icons .w-circ.five{
      background-image: url('./assets/10_original.webp');
}


```


# How to add Gradient in CSS
```
background : linear-gradient(to right, #color_one, #color_two); 
background : radial-gradient(circle, #color_one, #color_two); 
```

# Horizontal Row CSS properties 
***TAG :***  `<hr>` 

 **properties:**
```
	border : none; // removes the default border 
	border-top: 1px solid #000 ; // adds a top border with color.
			  : 2px dashed/dotted black ; 
			  
		width: 50% ; 
		height: 5px; 
		margin : 0 auto ; // center aligns the hr. 

	background-color: white; 
```



# Initial CSS code : 
```c
/* including font  */
@font-face {
    font-family: NunitoSans;
    src: url(./assets/fonts/NunitoSans.ttf);
}
@font-face {
    font-family: Roboto;
    src: url(./assets/fonts/Roboto.ttf);
}
@font-face {
    font-family: RobotoCondensed;
    src: url(./assets/fonts/RobotoCondensed.ttf);
}

/* CSS Variables  */
:root{
 /* color variables */
     --black: #000000 ;
    --darker: #012326 ; 
    --dark: #013a40 ; 
    --mid: #025e73 ; 
    --light: #4193a6 ; 
    --lighter: #84b9bf ; 
    --white: #ffffff ;
 /* font-variables  */
    --font-size: 1.3rem ;
    --robo: Roboto ;
    --Nuno: NunitoSans  ;
}

/* CSS Normalization / border-box model  */
html{
    box-sizing: border-box;
}

*, 
*::before,
 *::after{
    box-sizing: inherit;
 }

body{
    padding: 0 ; 
    margin : 0 ; 
    font-family: 'Robot', 'NunitoSans', 'RobotoCondensed' ; 
}

```

# Screen reader percautions for icons 

While using icons, make them invisible for screen-readers and instead add a sr-only class to some text after that. 

**ICON**
```c
<i class="fa-brands fa-linkedin" aria-hidden="true">
```

**Text with Icon (alt text  for icon) for  Screen Readers**
```c
<span class="sr-only">ICON</span>  //this will make it visible to scree readers only
```
