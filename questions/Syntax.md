Syntax
======

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
