### 170 Points

```js
function fitsInOneBox(boxes) {
  return boxes
    .sort((a, b) => a.l - b.l)
    .every((currentBox, i) => {
      if (i === 0) return true;
      const previousBox = boxes[i-1];
    
      return previousBox.l < currentBox.l && previousBox.w < currentBox.w && previousBox.h < currentBox.h;
  });
}
```
