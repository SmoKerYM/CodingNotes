# How to fetch data with 'async'?

```jsx
// useState variables
const [posts, setPosts] = useState([]);
const [loading, setLoading] = useState(false);

// fetch and inject data
useEffect(() => {
  const fetchPosts = async () => {
    setLoading(true);
    const res = await axios.get("https://jsonplaceholder.typicode.com/posts");
    setPosts(res.data);
    setLoading(false);
  };

  fetchPosts();
}, []
```

## Why use async?

Javascript is a single-thread programming language. If directly fetch without `async` may cause the un-interactive of the GUI.

```jsx
// useState variables
const [posts, setPosts] = useState([]);

// fetch and inject data
useEffect(() => {
  fetch("https://jsonplaceholder.typicode.com/posts")
    .then((response) => response.json())
    .then((response) => {
      setPosts(response);
    });
}, []);
```

This may cause user waiting, especially when the distance between the user and the server is considerably huge.
