# Questions about Routing in React

## I. How to link the jsx component with the routes?

1. Create a `markup.jsx` and add this component into the `App.js` file

   ```JSx
   function App() {
     return (
       <div className="page-wraper">
         <Markup />
       </div>
     );
   }

   export default App;
   ```
2. Import all components into the `markup.jsx` file and the required libraries

   ```jsx
   import React from "react";
   import { BrowserRouter, Route, Switch } from "react-router-dom";

   // Home Pages
   import IndexInfoMatrix from "./pages-infoMatrix/index-infoMatrix";

   // Other Pages...
   ```
3. Use BrowseRouter to set the routes

   ```jsx
   function Markup(){
     return(
       <>
           <BrowserRouter basename={""}>
             <Switch>
               {/* Home Pages */}
               <Route path="/" exact component={IndexInfoMatrix} />

               {/* Question Bank */}
               <Route path="/question-bank" exact component={QuestionBank} />
               <Route path="/specific-question/:q_id" exact component={SpecificQuestion} />

               {/* Forum */}
               <Route path="/forum" exact component={ForumIndex} />
               <Route path="/forum/study" exact component={ForumStudy} />
               <Route path="/forum/job" exact component={ForumJob} />
               <Route path="/forum/study/:org_id/post/:post_id" exact component={ForumSpecific} />
               <Route path="/forum/job/:org_id/post/:post_id" exact component={ForumSpecific} />
               <Route path="/forum/study/:org_id" exact component={ForumSpecificOrg} />
               <Route path="/forum/job/:org_id" exact component={ForumSpecificOrg} />

             </Switch>

             <PageScrollTop />
           </BrowserRouter>

           <BackToTop />
         </>
     );
   }
   ```

## II. How to specify url in the `<Link to"">` element?

### 2.1 Basic case:

```jsx
<Link to="/">
  <b>Home</b>
</Link>
```

### 2.2 How to send and receive information by the URL?

In the current component:

```jsx
<Link to={"/forum/study/" + this_school.id}>
  See Details
</Link>
```

In the target component:

```jsx
import { useParams } from 'react-router-dom';

function ForumSpecificOrg(){
  // Store the information from url to the variable `org_id`
  const { org_id } = useParams();

  // Using the passed in infomation
  const [id, setId] = useState(org_id);
}
```

### 2.3 How to send the infomation without explicitly showing it in the URL?

In the current component: specifing the 'state' attribute of the `to`, the data should be stored in key: value pair.

```jsx
<Link to={{
  pathname: '/postDetails',
  state: { orgId: org_id }
}}>
  View Post
</Link>
```

In the target component:

```jsx
import { useLocation } from 'react-router-dom';

function PostDetails() {
  const location = useLocation();
  const org_id = location.state.orgId || {}; // Default to empty object if state is undefined
  
  return <div>Organization ID: {org_id}</div>;
}
```
