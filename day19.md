# Challenge #19: Sorting the toys!

### Cognitive Complexity: 1 (>3000 ops/s)

```js
function sortToys(toys, positions) {
  return [...positions]
    .sort((a, b) => a - b)
    .map(v => toys[positions.indexOf(v)])
}
```
