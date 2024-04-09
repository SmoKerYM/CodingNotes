# How to achieve pagination in React?

It is quite common that when developer wants to show products in a specific page, but the number of which is too much to fit into a single page, or it will damage the user experience by "endless scrolling".

Therefore, we can implement pagination in React with a library `react-paginate` 

## Step 1: Install react-paginate

```
npm install react-paginate --save
```

P.S. if the required React version have conflit with the current React version in the project, you can use `--force` instead (not recommend)

```
npm install react-paginate --force
```

## Step 2: Import Libraries

```jsx
import React, { useEffect, useState } from "react";
import ReactPaginate from "react-paginate";
import QuestionCard from "./question-card";
```

The `QuestionCard` here is the single component used to show "an object", which can be replaced by your component.

## Step 3: The `PaginatedItems` component

```jsx
/**
 * Show the paginated items and the page numbers
 * @param {int} itemPerPage
 * @param {Array} item_fetched - items passed in from the parent 
 * @param {String} itemType - identifier of the type of layout of the item
 */

function PaginatedItems({ itemsPerPage, item_fetched, itemType }) {

  // Create and assign value to 'items' useState variable
  const [items, setItems] = useState([]);
  useEffect(() => setItems(item_fetched), [item_fetched]);

  // Represents the starting index of the object presenting
  const [itemOffset, setItemOffset] = useState(0);
  // Represents the ending index
  const endOffset = itemOffset + itemsPerPage;
  console.log(`Loading items from ${itemOffset} to ${endOffset}`);

  // Slice out the presented items
  const currentItems = items.slice(itemOffset, endOffset);
  const pageCount = Math.ceil(items.length / itemsPerPage);

  // Invoke when user click to request another page.
  const handlePageClick = (event) => {
    const newOffset = (event.selected * itemsPerPage) % items.length;
    console.log(
      `User requested page number ${event.selected}, which is offset ${newOffset}`
    );
    setItemOffset(newOffset);
  };

  return (
    <>  
    </>
  );
}
```

## Step 4: Write the return elements:

```jsx
return (
    <>
      {/* The items */}
      <div className="row">
        {/* If the itemType is question */}
        {currentItems &&
          itemType === "question" &&
          currentItems.map((this_question) => (
            <QuestionCard this_question={this_question} />
          ))}
      </div>
      {/* The pagination buttons */}
      <div className="row">
        <ReactPaginate
          breakLabel="..."
          nextLabel="Next >"
          onPageChange={handlePageClick}
          pageRangeDisplayed={5}
          pageCount={pageCount}
          previousLabel="< Prev"
          renderOnZeroPageCount={null}
	  containerClassName="pagination-container"
          pageClassName="pagination-page"
          activeClassName="pagination-active"
          previousClassName="pagination-previous"
          nextClassName="pagination-next"
        />
      </div>
    </>
  );
```

## Step 5: Add CSS styles

```css
/* Pagination */
.pagination-container {
  display: flex;
  list-style-type: none;
  padding: 0;
  justify-content: center; /* This centers your pagination controls */
}

/* Styles for the pagination items (numbers) */
.pagination-page {
  margin: 3px;
  padding: 5px 15px;
  border-radius: 4px;
  border: 1px solid #ddd;
  cursor: pointer;
}

/* Styles for the active page */
.pagination-active {
  background-color: var(--primary);
  color: #fff;
  border: 1px solid var(--primary);
}

/* Styles for the links inside the pagination items */
.pagination-page a {
  text-decoration: none;
  color: inherit;
}

/* Hover and active states */
.pagination-page:hover,
.pagination-page:active {
  background-color: var(--primary);
  color: #fff;
}

/* Styles for previous and next buttons */
.pagination-previous,
.pagination-next {
  padding: 5px 10px;
  font-weight: bold;
  border: 1px solid #ddd; /* Assuming you want borders */
  margin: 3px; /* To keep consistency with the pagination-page items */
  border-radius: 4px; /* To keep consistency with the pagination-page items */
  cursor: pointer; /* To indicate these are clickable */
}

.pagination-previous:hover, 
.pagination-next:hover {
  color: #fff;
  background-color: #f7b205;
}

/* Disabled state for previous and next buttons, if you need it */
.pagination-previous.disabled,
.pagination-next.disabled {
  color: #fff;
  cursor: not-allowed;
}
.pagination-previous.disabled a,
.pagination-next.disabled a{
  cursor: not-allowed;
}
```

## Step 6: Import and use the `PaginatedItems` Component

```jsx
import PaginatedItems from "../elements/question/pagination";

<PaginatedItems
    itemsPerPage={6}
    item_fetched={questions}
    itemType={"question"}
/>
```


---

Reference: https://www.npmjs.com/package/react-paginate
