# Challenge #7: Doing gifts inventory

### Cognitive Complexity: 1 (>1000 ops/s)

```js
function getGiftsToRefill(a1, a2, a3) {
  return [...(new Set(a1.concat(a2,a3)))]
    .filter((g) => a1.includes(g) + a2.includes(g) + a3.includes(g) === 1);
}
```
