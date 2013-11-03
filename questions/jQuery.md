jQuery
=========

#####1. How do I select elements when I already have a DOM element?

If you have a variable containing a DOM element, and want to select elements related to that DOM element, 
simply wrap it in a jQuery object.

```javascript
  var myDomElement = document.getElementById( "foo" ); // A plain DOM element.
 
  $( myDomElement ).find( "a" ); // Finds all anchors inside the DOM element.
  Many people try to concatenate a DOM element or jQuery object with a CSS selector, like so:
  
  $( myDomElement + ".bar" ); // This is equivalent to $( "[object HTMLElement].bar" );
  Unfortunately, you cannot concatenate strings to objects.
```

#####2. How do I test whether an element has a particular class?

.hasClass() (added in version 1.2) handles this common use case:

```javascript
  $( "div" ).click(function() {
      if ( $( this ).hasClass( "protected" ) ) {
          $( this )
              .animate({ left: -10 })
              .animate({ left: 10 })
              .animate({ left: -10 })
              .animate({ left: 10 })
              .animate({ left: 0 });
      }
  });
```

You can also use the .is() method along with an appropriate selector for more advanced matching:

```javascript
  if ( $( "#myDiv" ).is( ".pretty.awesome" ) ) {
      $( "#myDiv" ).show();
  }
```

Note that this method allows you to test for other things as well. 
or example, you can test whether an element is hidden (by using the custom :hidden selector):

```javascript
  if ( $( "#myDiv" ).is( ":hidden" ) ) {
      $( "#myDiv" ).show();
  }
```

#####3. How do I test whether an element exists?

Use the .length property of the jQuery collection returned by your selector:

```javascript
  if ( $( "#myDiv" ).length ) {
      $( "#myDiv" ).show();
  }
```

Note that it isn't always necessary to test whether an element exists. 
The following code will show the element if it exists, and do nothing (with no errors) if it does not:

```javascript
  $( "#myDiv" ).show();
```
#####4. How do I determine the state of a toggled element?

You can determine whether an element is collapsed or not by using the :visible and :hidden selectors.

```javascript
  var isVisible = $( "#myDiv" ).is( ":visible" );
  var isHidden = $( "#myDiv" ).is( ":hidden" );
```

If you're simply acting on an element based on its visibility, 
just include :visible or :hidden in the selector expression. For example:

```javascript
  $( "#myDiv:visible" ).animate({
      left: "+=200px"
  }, "slow" );
```
#####5. How do I select an element by an ID that has characters used in CSS notation?

Because jQuery uses CSS syntax for selecting elements, some characters are interpreted as CSS notation. 
For example, ID attributes, after an initial letter (a-z or A-Z), may also use periods and colons, 
in addition to letters, numbers, hyphens, and underscores (see W3C Basic HTML Data Types). 
The colon (":") and period (".") are problematic within the context of a jQuery selector because 
they indicate a pseudo-class and class, respectively.

In order to tell jQuery to treat these characters literally rather than as CSS notation, they must be "escaped" 
by placing two backslashes in front of them.

```javascript
  // Does not work:
  $( "#some:id" )
   
  // Works!
  $( "#some\\:id" )
   
  // Does not work:
  $( "#some.id" )
   
  // Works!
  $( "#some\\.id" )
```

The following function takes care of escaping these characters and places a "#" at the beginning of the ID string:

```javascript
  function jq( myid ) {
      return "#" + myid.replace( /(:|\.|\[|\])/g, "\\$1" );
  }
```

The function can be used like so:
```javascript
  jq( "some.id" ) )
```

#####6. How do I disable/enable a form element?

You can enable or disable a form element using the .prop() method:

```javascript
  // Disable #x
  $( "#x" ).prop( "disabled", true );
   
  // Enable #x
  $( "#x" ).prop( "disabled", false );
```

#####7. How do I check/uncheck a checkbox input or radio button?

You can check or uncheck a checkbox element or a radio button using the .prop() method:

```javascript
  // Check #x
  $( "#x" ).prop( "checked", true );
   
  // Uncheck #x
  $( "#x" ).prop( "checked", false );
```
#####8. How do I get the text value of a selected option?

Select elements typically have two values that you want to access. First there's the value to be sent to the server, 
hich is easy:

```javascript
  $( "#myselect" ).val();
  // => 1
```
The second is the text value of the select. For example, using the following select box:

```html
  <select id="myselect">
      <option value="1">Mr</option>
      <option value="2">Mrs</option>
      <option value="3">Ms</option>
      <option value="4">Dr</option>
      <option value="5">Prof</option>
  </select>
```
If you wanted to get the string "Mr" if the first option was selected (instead of just "1") you would do that
in the following way:

```javascript
  $( "#myselect option:selected" ).text();
  // => "Mr"
```
#####9. How do I replace text from the 3rd element of a list of 10 items?

Either the :eq() selector or the .eq() method will allow you to select the proper item. 
owever, to replace the text, you must get the value before you set it:

```javascript
  // This doesn't work; text() returns a string, not the jQuery object:
  $( this ).find( "li a" ).eq( 2 ).text().replace( "foo", "bar" );
   
  // This works:
  var $thirdLink = $( this ).find( "li a" ).eq( 2 );
   
  var linkText = $thirdLink.text().replace( "foo", "bar" );
   
  $thirdLink.text( linkText );
```
The first example just discards the modified text. The second example saves the modified text and then 
eplaces the old text with the new modified text. Remember, .text() gets; .text( "foo" ) sets.

#####10. How do I pull a native DOM element from a jQuery object?

A jQuery object is an array-like wrapper around one or more DOM elements. 
To get a reference to the actual DOM elements (instead of the jQuery object), you have two options. 
The first (and fastest) method is to use array notation:

```javascript
  $( "#foo" )[ 0 ]; // Equivalent to document.getElementById( "foo" )
  The second method is to use the .get() function:
  
  $( "#foo" ).get( 0 ); // Identical to above, only slower.
```
You can also call .get() without any arguments to retrieve a true array of DOM elements.

#####11. How do I create a jQuery plugin?

Sometimes you want to make a piece of functionality available throughout your code. 
For example, perhaps you want a single method you can call on a jQuery selection that performs a series of 
operations on the selection. 
Maybe you wrote a really useful utility function that you want to be able to move easily to other projects. 
In this case, you may want to write a plugin.

######How jQuery Works 101: jQuery Object Methods and Utility Methods

Before we write our own plugins, we must first understand a little about how jQuery works. Take a look at this code:

```javascript
  $( "a" ).css( "color", "red" );
```
This is some pretty basic jQuery code, but do you know what's happening behind the scenes? 
Whenever you use the $ function to select elements, it returns a jQuery object. 
This object contains all of the methods you've been using (.css(), .click(), etc.) and all of the elements that fit 
your selector. The jQuery object gets these methods from the $.fn object. 
This object contains all of the jQuery object methods, and if we want to write our own methods, 
it will need to contain those as well.

Additionally the jQuery utility method $.trim() is used above to remove any leading or trailing empty space characters 
from the user input. Utility methods are functions that reside directly in the $ function itself. 
You may occasionally want to write a utility method plugin when your extension to the jQuery API does not have to do 
something to a set of DOM elements you've retrieved.

######Basic Plugin Authoring

Let's say we want to create a plugin that makes text within a set of retrieved elements green. 
All we have to do is add a function called greenify to $.fn and it will be available just like any other jQuery object 
method.

```javascript
  $.fn.greenify = function() {
      this.css( "color", "green" );
  };

  $( "a" ).greenify(); // Makes all the links green.
```
Notice that to use .css(), another method, we use this, not $( this ). 
This is because our greenify function is a part of the same object as .css().

######Chaining

This works, but there's a couple of things we need to do for our plugin to survive in the real world. 
One of jQuery's features is chaining, when you link five or six actions onto one selector. 
This is accomplished by having all jQuery object methods return the original jQuery object again (there are a few 
exceptions: .width() called without parameters returns the width of the selected element, and is not chainable). 
Making our plugin method chainable takes one line of code:

```javascript
  $.fn.greenify = function() {
      this.css( "color", "green" );
      return this;
  }

  $( "a" ).greenify().addClass( "greenified" );
```
Note that the notion of chaining is not applicable to jQuery utility methods like $.trim().

######Protecting the $ Alias and Adding Scope

The $ variable is very popular among JavaScript libraries, and if you're using another library with jQuery, 
you will have to make jQuery not use the $ with jQuery.noConflict(). 
However, this will break our plugin since it is written with the assumption that $ is an alias to the jQuery function. 
To work well with other plugins, and still use the jQuery $ alias, we need to put all of our code inside of an 
Immediately Invoked Function Expression, and then pass the function jQuery, and name the parameter $:

```javascript
  (function ( $ ) {
   
    $.fn.greenify = function() {
      this.css( "color", "green" );
      return this;
    };
    
    $.ltrim = function( str ) {
      return str.replace( /^\s+/, "" );
    };
    
    $.rtrim = function( str ) {
      return str.replace( /\s+$/, "" );
    };
   
  }( jQuery ));
```

In addition, the primary purpose of an Immediately Invoked Function is to allow us to have our own private variables. 
Pretend we want a different color green, and we want to store it in a variable.

```javascript
  (function ( $ ) {
   
    var shade = "#556b2f";
    $.fn.greenify = function() {
      this.css( "color", shade );
      return this;
    };
  }( jQuery ));
```

######Minimizing Plugin Footprint

It's good practice when writing plugins to only take up one slot within $.fn. 
This reduces both the chance that your plugin will be overridden, and the chance that your plugin will 
override other plugins. In other words, this is bad:

```javascript
  (function( $ ) {
    $.fn.openPopup = function() {
        // Open popup code.
    };
 
    $.fn.closePopup = function() {
        // Close popup code.
    };
  }( jQuery ));
```

It would be much better to have one slot, and use parameters to control what action that one slot performs.

```javascript
  (function( $ ) {
    $.fn.popup = function( action ) {
      if ( action === "open") {
          // Open popup code.
      }
      if ( action === "close" ) {
          // Close popup code.
      }
    };
  }( jQuery ));
```
######Using the each() Method

Your typical jQuery object will contain references to any number of DOM elements, and that's why jQuery objects are 
often referred to as collections. If you want to do any manipulating with specific elements (e.g. getting a data 
attribute, calculating specific positions) then you need to use .each() to loop through the elements.

```javascript
  $.fn.myNewPlugin = function() {
    return this.each(function() {
        // Do something to each element here.
    });
  };
```
Notice that we return the results of .each() instead of returning this. 
Since .each() is already chainable, it returns this, which we then return. 
This is a better way to maintain chainability than what we've been doing so far.

######Accepting Options

As your plugins get more and more complex, it's a good idea to make your plugin customizable by accepting options. The easiest way do this, especially if there are lots of options, is with an object literal. Let's change our greenify plugin to accept some options.
```javascript
  (function ( $ ) {
   
    $.fn.greenify = function( options ) {
      // This is the easiest way to have default options.
      var settings = $.extend({
        // These are the defaults.
        color: "#556b2f",
        backgroundColor: "white"
      }, options );
  
      // Greenify the collection based on the settings variable.
      return this.css({
        color: settings.color,
        backgroundColor: settings.backgroundColor
      });
    };
    
  }( jQuery ));
``` 
######Example usage:

```javascript
  $( "div" ).greenify({
      color: "orange"
  });
```
The default value for color of #556b2f gets overridden by $.extend() to be orange.

Putting It Together
Here's an example of a small plugin using some of the techniques we've discussed:
```javascript
  (function( $ ) {
   
    $.fn.showLinkLocation = function() {
      return this.filter( "a" ).each(function() {
        $( this ).append( " (" + $( this ).attr( "href" ) + ")" );
      });
    };
   
  }( jQuery ));

  // Usage example:
  $( "a" ).showLinkLocation();
```
This handy plugin goes through all anchors in the collection and appends the href attribute in brackets.

```html
<!-- Before plugin is called: -->
<a href="page.html">Foo</a>
 
<!-- After plugin is called: -->
<a href="page.html">Foo (page.html)</a>
Our plugin can be optimized though:
```
```javascript
  (function( $ ) {
   
    $.fn.showLinkLocation = function() {
      return this.filter( "a" ).append(function() {
        return " (" + this.href + ")";
      });
    };
   
  }( jQuery ));
```
We're using the .append() method's capability to accept a callback, and the return value of that callback will 
determine what is appended to each element in the collection. 
Notice also that we're not using the .attr() method to retrieve the href attribute, 
because the native DOM API gives us easy access with the aptly named href property.
