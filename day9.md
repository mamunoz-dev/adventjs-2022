# Challenge #9: Crazy Xmas lights

### Cognitive Complexity: 1 (>2000 ops/s)

```js
function countTime(leds) {
  return leds.join('').repeat(2).split(/1/).sort().pop().length * 7;
}
```
