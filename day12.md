# Challenge #12: Electric sleighs, wow!

### Cognitive Complexity: 1 (>3000 ops/sec)

```js
function selectSleigh(distance, sleighs) {
  return sleighs
    .filter(sleigh => sleigh.consumption*distance <= 20)
    .map(sleigh => sleigh.name)
    .pop() || null;
}
```
