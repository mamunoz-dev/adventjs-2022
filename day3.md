### 198 points

```js
distributeGifts = (packOfGifts, reindeers) => {
  const packOfGiftsWeight = packOfGifts.reduce((acc, gift) => acc + gift.length, 0);
  const reindeersWeightLimit = reindeers.reduce((acc, reindeer) => acc + 2*reindeer.length, 0);
  
  return Math.floor(reindeersWeightLimit/packOfGiftsWeight);
}
```

### 198 points

```js
distributeGifts = (packOfGifts, reindeers) => {
  const packOfGiftsWeight = packOfGifts.toString().length - packOfGifts.length + 1;
  const reindeersWeightLimit = (reindeers.toString().length - reindeers.length + 1)*2
  
  return Math.floor(reindeersWeightLimit/packOfGiftsWeight);
}
```

### 198 points (sent by @corteshvictor from Discord)

```js

distributeGifts = (packOfGifts, reindeers) => {
  const packOfGiftsSize = packOfGifts.join('').length;
  const reindeersSize = reindeers.join('').length * 2;
  
  return Math.floor(reindeersSize / packOfGiftsSize)
}
```
