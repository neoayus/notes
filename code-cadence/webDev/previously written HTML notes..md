#html #old-notes 
<!DOCTYPE html> : describes document type 
<html> container for code 
<head> Containds metadata 
    <title> : title of webpage 

<body>
    <p> : to write paragraph 
    <img> to bring image 
    <a> : for hyperlinks  

    <sub> : subscipt 
    <sup> : superscript
    
    <b> : bold
    <i> : italic 
    <u> : underline
    
    <div> : to create division but is Block element 
    <span> : to create division but it's Inline element 

SYMANTIC TAGS : markup that relates to meaning of content 
NON SYMANTIC : exact opposite 

SEO friendly : search engine optimization 

    <header> : header of webpage 
    <main> : main content of website 
    <footer> : footer of website  
    <nav> : for navigations
    <article> : to add article 
    <section> : to group together other elements 
    <aside> : realted links / contents
    
Entities : are string that starts with & and ends with ; and are used to display reserved character on screen like : &nbsp ; 

Emmet : visit emmet.io

<table> : to design table 
    <caption> : writ table caption 
    <tr> : table row 
    <th> : table header 
    <tr> : table row
        // Semantics in table 
    <thead> : table head 
    <tbody> : body of table 
    <tfoot> : table footer 
        
        //attributes
    colspan = "" : column span
    rowspan = "" : row span 

<form> : to create forms 
    <form action=""> : defines action to be performed when submittion of form
    <input> : to create multiple form form controls
    <input type=""> : important attribute 
            type = text ; 
            type = password ; 
            type = number ; 
            type = time ; 
            type = color ; 
            type = butto : to create buttons 
            type = submit : to create butto that submits data to server
            type = checkbox : creates a checkbox. 
            type = radio : to create radio buttons 
                (we can group both, radio buttons checkboxes)
            type = range : to specify a range
                min="" : minimum value 
                max="" : maximum value 
                step="" : sets value of steps to skip 
                value="" : default value 
            
            
            name : used to assign name to values as : NAME = VALUE. 
            
            

            
    <input placeholder = ""> : text stored in input box 

    <label> : represents an caption for the form element/item in ui
    
    <button> : creates a button that performs a specific task 
        <button type ="submit"> : to submit data to serever 
        <button type ="button"> : do something 
        <button type ="reset"> : reset all the values in the forum existing currently :3

    <select> : used to create dropdowns 
            <select name="" id="" > : NAME = ID ;
        <option value=""> : name=value. 
            <option value="" selected> : will set this to default value 

    <textarea> : to specify an area to write bunch of paragraphs 
            rows : to specify area 
            columns : to specify area of text 
            placeholder : write your feedback here 
