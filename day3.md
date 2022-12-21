# Challenge #3: How many packs of gifts can Santa carry?

### Cognitive Complexity: 1 (>3000 ops/s)

```js
function distributeGifts(packOfGifts, reindeers) {
  return Math.floor(
    reindeers.reduce((acc, reindeer) => acc + 2*reindeer.length, 0) /
    packOfGifts.reduce((acc, gift) => acc + gift.length, 0));
}
```
