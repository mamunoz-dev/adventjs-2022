# Challenge #6: Creating xmas decorations

### Cognitive Complexity: 1 (~300 ops/s)

```js
function createCube (size) {
  const repeat = (str, times) => str.repeat(times);
  
  return Array.from(new Array(size))
    .reduce((acc, curr, i) => {
      return [
        acc[0] + repeat(' ', size-i-1) + 
        repeat('/\\', i+1) + repeat('_\\', size) + '\n',
        acc[1] + repeat(' ', i) + 
        repeat('\\/', size-i) + repeat('_/', size) + '\n',
      ]
    }, ['', '']).join('').replace(/\n$/, "");
}
```
