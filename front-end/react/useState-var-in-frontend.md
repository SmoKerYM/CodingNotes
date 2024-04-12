# Why the element is not updated automatically when useState change?

Original Code:

```jsx
<h1>
    <Count counter={posts.length} />
    <h4>Discussions</h4>
</h1>
```

The useState variable `posts` should change after fetching data from the server, so as the `posts.length`, but the element is not updated.

## Solution:

Use a [condition statement]() to avoid the base case, make sure the element is rendered after the `posts` have received data from the server.

```jsx
<h1>
    {posts.length !== 0 && <Count counter={posts.length} /> } 
    <h4>Discussions</h4>
</h1>
```
