How to store and read cookies using js

1. Use cookies.js - a simple cookie reader/writer framework by Mozilla 
    -> https://developer.mozilla.org/en-US/docs/Web/API/Document/cookie/Simple_document.cookie_framework
    
2. Set a cookie:
   docCookies.setItem(cookie_name, cookie_value, time_till_expiration, path, domain, secure); 
   // cookie_name = string
   // cookie_value = string
   // time_till_expiration (optional) = in seconds (e.g. 31536e3 for a year, 'Infinity' etc), or as js Date object
   // path (optional) = the absolute path from where the cookie will be readable (string)
   // domain (optional) = domain from where cookie will be readable (string)
   // secure (optional) = boolean. The cookie will be transmitted only over secure protocol.
   
  3. Get a cookie:
     docCookies.getItem(name)
     // if doesn't exist, returns null
     
  4. Delete a cookie:
     docCookies.removeItem(name[, path[, domain]])
     
  5. List all cookies:
     docCookies.keys()
   
