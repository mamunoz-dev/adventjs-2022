### 260 points

```js
function checkJump(heights) {
  const max = Math.max(...heights)
  const maxIndex = heights.indexOf(max);
  
  const left = heights.slice(0, maxIndex);
  const right = heights.slice(maxIndex+1);
  
  const leftAllWayUp = left.slice(1).every((item, i) => item >= left[i]);
  const rightAllWayDown = right.slice(1).every((item, i) => item <= right[i]);
  
  return left.length > 0 && right.length > 0 && leftAllWayUp && rightAllWayDown;
}
```
