JavaScript and jQuery questions and answers
=====================================

Compilation of JavaScript and jQuery interview questions and answers.

Index
-----


Theorical
---------

1. What is JavaScript?

  JavaScript is a prototype-based, interpreted programming with dynamic typing and has first-class functions. 
  This language is most often used for client-side web development.

2. What is the difference between JavaScript and Jscript? 

  Both JavaScript and Jscript are similar. JavaScript was developed by Netscape. 
  JScript is Microsoft's dialect of the ECMAScript standard that is used in Microsoft's Internet Explorer.
  
3. Which are JavaScripts's primitive datatypes?

  String, Number, Boolean, Array, Object, Null, Undefined.

```javascript
  typeof new String('foo'); // "object" <-- This is called a primitive wrapper
  typeof 'foo'; // "string"
```

4. Does JavaScript Support automatic type conversion?.

  Yes, Javascript support automatic type conversion.
  
```javascript
  var s = '5';
  var a = s*1;
  var b = +s;
  typeof(s); //"string"
  typeof(a); //"number"
  typeof(b); //"number"
```

Syntax
------

1. What is the difference between “==” and “===”? 
  
  == checks equality only, 
  === checks for equality as well as the type.

2. How do you get a Checkbox's status? (whether it is checked or not)

```javascript
  var status = document.getElementById('checkbox1').checked; 
  alert(status); 
```
  
3. What does isNaN function do? 

  It returns true if the argument is not a number.

```javascript
  document.write(isNaN("Hello")+ "<br>"); //true
  document.write(isNaN("2013/06/23")+ "<br>"); //true
  document.write(isNaN(123)+ "<br>"); //false
```

4. How do you change the style/class on any element using only JavaScript? 

```javascript
  document.getElementById(“myText”).style.fontSize = “10";
  //or
  document.getElementById(“myText”).className = “anyclass”; 
```

Sources
-------

- http://www.codeproject.com/Articles/620811/Latest-JavaScript-Interview-Questions-and-Answers
- 
