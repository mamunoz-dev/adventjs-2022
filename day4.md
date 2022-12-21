# Challenge #4: Box inside a box and another...

### Cognitive Complexity: 1 (> 2000 ops/s)

```js
function fitsInOneBox(boxes) {
  return boxes
    .sort((a, b) => a.l - b.l)
    .every((currentBox, i) => {
      return i === 0 || ( 
        boxes[i-1].l < currentBox.l && 
        boxes[i-1].w < currentBox.w && 
        boxes[i-1].h < currentBox.h);
  });
}
```
