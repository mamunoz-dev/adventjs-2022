# Challenge #18: We ran out of ink!

### Cognitive Complexity: 1 (>1000 ops/s)

```js
function dryNumber(dry, numbers) {
  return Array.from(Array(numbers))
    .map((item, i) => i+1)
    .filter(item => item.toString().includes(dry));
}
```
