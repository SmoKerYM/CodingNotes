# How to use fontAwesome elements in React?

1. Add SVG core

   ```
   npm i --save @fortawesome/fontawesome-svg-core
   ```
2. Add Icon Packages

   ```
   npm i --save @fortawesome/free-solid-svg-icons
   npm i --save @fortawesome/free-regular-svg-icons
   npm i --save @fortawesome/free-brands-svg-icons
   ```
3. Install React Component

   ```
   npm i --save @fortawesome/react-fontawesome@latest
   ```
4. Go into a jsx file, import the icon(s)

   ```
   import { FontAwesomeIcon } from '@fortawesome/react-fontawesome';
   import { faSpinner } from '@fortawesome/free-solid-svg-icons';
   ```

    Take 'faSpinner' as an example

5. Use the element in the `return` part of react component

   ```jsx
   return (
       <div>
         <FontAwesomeIcon icon={faSpinner} spin/>
       </div>
     );
   ```

   `spin` make the icon keep spinning...

---

Reference: https://docs.fontawesome.com/web/use-with/react/
