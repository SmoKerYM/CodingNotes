# How to customize port number for React App?

It is quite usual that we need to run two distinct React App at the same time, but the default port number of React app is 3000. Therefore, without specifying another port number for one of the app can cause port conflict.

## Solution:

Change the port numberr of the React App.

1. Install `cross-env`

   ```bash
   npm install cross-env
   ```
2. Add `cross-env PORT=3001 ` the  `"scripts" -> "start" `in the file  `package.json`

   ```json
   "scripts": {
       "start": "cross-env PORT=3001 react-scripts start",
       "build": "react-scripts build",
       "test": "react-scripts test",
       "eject": "react-scripts eject",
       "ghp": "react-scripts build && gh-pages -d build"
     },
   ```

    3. After using`npm start`, the port number will be changed.
