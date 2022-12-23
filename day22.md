# Challenge #22: The lights in sync

### Cognitive Complexity: 1 (>3000 ops/s)

```js
function checkStepNumbers(systemNames, stepNumbers) {
  const dict = [...new Set(systemNames)]
  .reduce((acc, v) => {
    acc[v] = [];
    return acc;
  }, {});
 
  const groups = systemNames.reduce((acc, elm, i) => {
    acc[elm].push(stepNumbers[i]);
    return acc;
  }, dict);
  
  return Object.values(groups)
    .map(arr => arr.every((x, i) => i === 0 || x >= arr[i-1]))
    .every(elm => elm);
}
```
