### the problem
- `package.json` contains lots of key config for your app, including build scripts, migration scripts, etc - important and complex
- `.json` files don't support comments.

### the solution

Convention in `package.json` - use the key `"//"`, then use the string value to contain your comment.
- You can have duplicate keys - your linter might complain, but it's valid json. 
- The devs of node have reserved `"//"` for comments
- use an array of strings for a multiline comment

e.g.
```
  "scripts": {
    "start:prod": "node ./build/server.js",
    "//": "start:prod: this is called by heroku to start the server, as specified in the Procfile",
    "start:dev": "nodemon --exec babel-node src/server.js",
    "//": [
      "start:local: uses nodemon to reload the server automatically when changes to the code are",
      "detected. Runs the es6 code (not transpiled) using babel-node (instead of node)."
    ],
    ...
  ```
