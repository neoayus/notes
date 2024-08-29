
## Indentation
4 tab indentation with : 
```
int main{
	return 0 ; 
}
```
## Naming Conventions: 

1. **File Name :**   'kebab' 
		`this-is-my-random-ahh-file.md`
		
1. **Class Name :** 'pascal' 
		`ThisIsAClassInCPP`
		
3. **Variable/Function Name :** 'camel' and 'snake' case 
		`int thiIsARandomNumber = 0 ` and `int this_is_a_Number`
		
4. **URL / CSS Class Names :*** 'kebab'  
			`.nav-options-first`


# HTML :
+ assign `role = "" ` to every div. 
# CSS : 
 #css 
+ Always use double quotes. 
+ prefer rem nd em > px. 
+ 
## BEM Convention 

BEM Stands for **Block Element Modification.** 

+ ***Block :***  `.block` or `.complex-block`
+ ***Element:***  `.block__elementt` or `.block__element`
+ ***Modifier :***  `.block__element--identifier` or `.complex-block`

```
<nav class="menu"> // block 
 <ul class="menu__list"> //element 
    <li class="menu__item menu__item--active">Home</li> //modifier
    <li class="menu__item">About</li>
    <li class="menu__item">Contact</li>
  </ul>
</nav>
```
## Declaration Order : 

CSS Comb Order: specific methodology developed by CSSComb. 

*example:* 
+ ***Positioning*** :  `position` `top` `right` `bottom` `left`
+ ***Box Model*** :  `display` `float` `width` `height` `margin` `padding` `border` `outline`
+ ***Typography*** :  `font-family` `font-size` `font-weight` `line-height` `text-align` `color`
+ ***Background*** : `background` `background-color` `background-image` 
+ ***Miscellaneous*** : `animation` `transform` `transition` `opacity` 

# JS 
#js #java_script  
+ Use :  ***"use strict" ;*** 
+ Arrow Functions 
+ ARIA ROLES 