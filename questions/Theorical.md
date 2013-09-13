Theorical
=========

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

#####4. Does JavaScript Support automatic type conversion?

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

#####9. How do JavaScript timers work? What is a drawback of JavaScript timers?

Timers allow you to execute code at a set time or repeatedly using an interval. 
This is accomplished with the setTimeout, setInterval, and clearInterval functions. 
The setTimeout(function, delay) function initiates a timer that calls a specific function after the delay; 
it returns an id value that can be used to access it later. 
The setInterval(function, delay) function is similar to the setTimeout function except that it executes repeatedly on the delay and only stops when cancelled. 
The clearInterval(id) function is used to stop a timer. 
Timers can be tricky to use since they operate within a single thread, thus events queue up waiting to execute.

#####10. What are JavaScript closures?

A closure is a special kind of object that combines two things: a function, and the environment in which that function was created. 
The environment consists of any local variables that were in-scope at the time that the closure was created.   
Consider the following example:
```javascript
  function makeAdder(x) {
    return function(y) {
      return x + y;
    };
  }
  
  var add5 = makeAdder(5);
  var add10 = makeAdder(10);
  
  print(add5(2));  // 7
  print(add10(2)); // 12
```
In this example, we have defined a function makeAdder(x) which takes a single argument x and returns a new function. 
In essence, makeAdder is a function factory (it creates functions which can add a specific value to their argument). 
In the above example we use our function factory to create two new functions (one that adds 5 to its argument, and one that adds 10).

add5 and add10 are both closures. 
They share the same function body definition, but store different environments. 
In add5's environment, x is 5. As far as add10 is concerned, x is 10.
