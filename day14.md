### 300 puntos (<3000 ops/sec, Complejidad Cognitiva: 1)

```js
function getOptimalPath(path) {
  return path
    .reverse()
    .reduce((acc, level) => {
      return level.map((num, i) => num + Math.min(acc[i], acc[i + 1]));
    })[0];
}
```
