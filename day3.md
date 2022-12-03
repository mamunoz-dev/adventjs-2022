### 198 puntos

```js
distributeGifts = (packOfGifts, reindeers) => {
  const packOfGiftsWeight = packOfGifts.reduce((acc, gift) => acc + gift.length, 0);
  const reindeersWeightLimit = reindeers.reduce((acc, reindeer) => acc + 2*reindeer.length, 0);
  
  return Math.floor(reindeersWeightLimit/packOfGiftsWeight);
}

const packOfGifts = ["book", "doll", "ball"]
const reindeers = ["dasher", "dancer"]

// el pack de regalos pesa 4 + 4 + 4 = 12
// los renos pueden llevar (2 * 6) + (2 * 6) = 24
// por lo tanto, Santa Claus puede entregar 2 cajas de regalos

console.log(distributedGifts(packOfGifts, reindeers)); // 2
```

### 198 puntos

```js
distributeGifts = (packOfGifts, reindeers) => {
  const packOfGiftsWeight = packOfGifts.toString().length - packOfGifts.length + 1;
  const reindeersWeightLimit = (reindeers.toString().length - reindeers.length + 1)*2
  
  return Math.floor(reindeersWeightLimit/packOfGiftsWeight);
}
```
