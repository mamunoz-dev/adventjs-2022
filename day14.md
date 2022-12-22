# Challenge #14: The best path

### Cognitive Complexity: 1 (>2000 ops/s)

```js
function getOptimalPath(path) {
  return path
    .reverse()
    .reduce((acc, level) => {
      return level.map((num, i) => num + Math.min(acc[i], acc[i + 1]));
    })[0];
}
```
