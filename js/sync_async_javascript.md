Javascript is normally blocking, single threaded.

There are special built in functions that are asynchronous, such as 
`setTimeOut` and AJAX requests. These are non-blocking, so subseqent
lines of code are executed before they return.

This means to check if a function is blocking or non-blocking, you need to look 
at its code and see if it calls any of Javascript's special async functions.

It would be interesting to look at the async functions' implementations to see 
how they work.

Promises therefore enable you to write explicit non-blocking code, and also
 (as is well known) write things neater to avoid 'callback hell'.
 
 Good articles:
 
 - [https://www.pluralsight.com/guides/front-end-javascript/introduction-to-asynchronous-javascript](https://www.pluralsight.com/guides/front-end-javascript/introduction-to-asynchronous-javascript)
 - [http://callbackhell.com/](http://callbackhell.com/)
 
