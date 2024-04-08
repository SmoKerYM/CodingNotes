## Add setUseState function to the `onClick()` function cause Too Many Re-renders.

```jsx
<button
    className={classNameTitle + " round-btn search-type-btn"}
    onClick={setSearchType("title")}
>
Title
</button>
```

### Reason:

Calling the setSearchType function directly inside the onClick attribute, which causes it to be executed immediately on each render, leading to infinite re-renders.

### Solution:

Pass a function to onClick that will be called when the button is clicked.

```jsx
<button
    className={classNameTitle + " round-btn search-type-btn"}
    onClick={() => setSearchType("title")}
>
Title
</button>
```
