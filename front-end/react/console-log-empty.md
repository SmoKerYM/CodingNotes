# Why the data is empty after fetching it from the server?

```jsx
const [data, setData] = useState([]);
const fetchData = async () => {
  setLoading(true);
  try {
    const res = await axios.get("/forum/organisation/" + id);
    setData(res.data);
    console.log(data) // log the data
  } catch (error) {
    console.error('Failed to fetch data:', error);
  } finally {
    setLoading(false);
  }
};
```

## Reason:

The setter method of the useState vairable will not be trigger untill finish running the rest of the program, so the `setData(res.data)` will not be execute before `console.log()`. Therefore the logged data will be `[]`.

## Solution:

To log a useState vairable after it is changed, you need to place the `console.log()` into another useEffect method.

```jsx
useEffect(() => {
  console.log(data);
}, [data]);
```

By putting `data` as the dependency of the useEffect() method, it will be executed automatically after the value of `data` changed, since achieving the logging of useState variables.
