Web
===

#####1. What is the difference between window.onload and onDocumentReady?

The onload event does not fire until every last piece of the page is loaded, this includes css and images, which means there’s a huge delay before any code is executed.
That isnt what we want. We just want to wait until the DOM is loaded and is able to be manipulated. onDocumentReady allows the programmer to do that.

#####2. What is unobtrusive JavaScript? How to add behavior to an element using JavaScript?

Unobtrusive Javascript refers to the argument that the purpose of markup is to describe a document’s structure, not its programmatic behavior and that combining the two negatively impacts a site’s maintainability. 
Inline event handlers are harder to use and maintain, when one needs to set several events on a single element or when one is using event delegation.