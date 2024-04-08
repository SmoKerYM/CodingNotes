### How can the `div` structure influence the position of elements?
When i write three buttons as the code below：
```html
<div>
    <button className="btn-warning round-btn search-type-btn">
    Title
    </button>
</div>
<div>
    <button className="btn-light round-btn search-type-btn">
    Content
    </button>
</div>
<div>
    <button className="btn-light round-btn search-type-btn">
    Tag
    </button>
</div>
```
The buttons are positioned at the center of the line:
![1710508230088](../image/div-and-layout/1710508230088.png)

But when i delete the `div` wrapper outside these three button, they kind of go wild.
```html
<button className="btn-warning round-btn search-type-btn">
    Title
</button>
<button className="btn-light round-btn search-type-btn">
    Content
</button>
<button className="btn-light round-btn search-type-btn">
    Tag
</button>
```
![1710508443932](../image/div-and-layout/1710508443932.png)

Seems like they just escape from the vertical center of the line, and their bottom border extends to the bottom of that line.
## And I don't know why...