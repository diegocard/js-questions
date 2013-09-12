JavaScript and jQuery questions and answers
=====================================

Compilation of JavaScript and jQuery interview questions and answers.

Index
-----


Theorical
---------

#####1. What is JavaScript?

  JavaScript is a prototype-based, interpreted programming with dynamic typing and has first-class functions. 
  This language is most often used for client-side web development.

#####2. What is the difference between JavaScript and Jscript? 

  Both JavaScript and Jscript are similar. JavaScript was developed by Netscape. 
  JScript is Microsoft's dialect of the ECMAScript standard that is used in Microsoft's Internet Explorer.
  
#####3. Which are JavaScripts's primitive datatypes?

  String, Number, Boolean, Array, Object, Null, Undefined.

```javascript
  typeof new String('foo'); // "object" <-- This is called a primitive wrapper
  typeof 'foo'; // "string"
```

#####4. Does JavaScript Support automatic type conversion?.

  Yes, Javascript support automatic type conversion.
  
```javascript
  var s = '5';
  var a = s*1;
  var b = +s;
  typeof(s); //"string"
  typeof(a); //"number"
  typeof(b); //"number"
```

#####5. What are global variables? How are they declared? What are the problems with using globals?

Global variables are available throughout your code: that is, the variables have no scope. Local variables scope, on the other hand, is restricted to where it is declared (like within a function). The var keyword is used to declare a local variable or object, while omitting the var keyword creates a global variable.
Global variables are widely considered as a bad practice, as they make your code unpredicatable and hard to maintain.

#####6. What is the difference between undefined and null?

The value of a variable with no value is undefined (i.e., it has not been initialized). Variables can be emptied by setting their value to null. 

#####7. What is JavaScript's this keyword?

JavaScript's this keyword normally refers to the object that owns the method, but it depends on how a function is called.
Basically, it points to the currently in scope object that owns where you are in the code.
When working within a Web page, this usually refers to the Window object. 
If you are in an object created with the new keyword, the this keyword refers to the object being created. 
When working with event handlers, JavaScript's this keyword will point to the object that generated the event.

#####8. What is event bubbling?

Event bubbling describes the behavior of events in child and parent nodes in the Document Object Model (DOM); 
that is, all child node events are automatically passed to its parent nodes. 
The benefit of this method is speed, because the code only needs to traverse the DOM tree once. 
This is useful when you want to place more than one event listener on a DOM element since you can put just one listener on all of the elements, 
thus code simplicity and reduction. One application of this is the creation of one event listener on a page's body element to respond to any click event that occurs within the page's body.

Syntax
------

#####1. What is the difference between “==” and “===”?
  
  == checks equality only, 
  === checks for equality as well as the type.

```javascript
  if (nullExample === null) { // executes this block only if null }
  if (undExample === Undefined) { // executes this block only if Undefined }
  if (bothExampe == null) { // executes this block if Undefined or null }
```

The big difference is the first uses coercion, which can have some odd results (it returns true for a null or undefined comparison if they are either).

#####2. How do you get a Checkbox's status? (whether it is checked or not)

```javascript
  var status = document.getElementById('checkbox1').checked; 
  alert(status); 
```
  
#####3. What does isNaN function do? 

  It returns true if the argument is not a number.

```javascript
  document.write(isNaN("Hello")+ "<br>"); //true
  document.write(isNaN("2013/06/23")+ "<br>"); //true
  document.write(isNaN(123)+ "<br>"); //false
```

#####4. How do you change the style/class on any element using only JavaScript? 

```javascript
  document.getElementById("myText").style.fontSize = "10";
  //or
  document.getElementById("myText").className = "anyclass"; 
```

Object oriented programming
---------------------------

#####1. Does JavaScript support OOP?

  Coming up
  
#####2. How does JavaScript inheritance work?

  Coming up

#####3. Example on how to emulate OOP behavior on JavaScript

  Coming up

Sources
-------

- http://www.codeproject.com/Articles/620811/Latest-JavaScript-Interview-Questions-and-Answers
- http://www.techrepublic.com/blog/software-engineer/javascript-interview-questions-and-answers/
