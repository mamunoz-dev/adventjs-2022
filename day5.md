# Challenge #5: Optimizing Santa's trips

### Cognitive Complexity: 1 (~20 ops/s)

```js
function getMaxGifts(giftsCities, maxGifts, maxCities) {
  return Math.max(0, ...(
    [...giftsCities
      .reduce((x, y) => x.concat(x.map(x => [y].concat(x))), [[]])]
      .filter((combi) => combi.length <= maxCities)
      .map((combi) => combi.reduce((acc, weight) => acc + weight, 0))
      .filter((item) => item <= maxGifts))
  );
}
```

### Iterative algorithm explained

With the following inputs:

```js
const giftsCities = [12, 3, 11, 5, 7]
const maxGifts = 20
const maxCities = 3
```

1) Get all possible combintions of elements in the array:

```js
[
[12],[3],[11],[5],[7],
[12,3],[12,11],[3,11],[12,5],[3,5],[11,5],[12,7],[3,7],[11,7],[5,7],
[12,3,11],[12,3,5],[12,11,5],[3,11,5],[12,3,7],[12,11,7],[3,11,7],[12,5,7],[3,5,7],[11,5,7],
[12,3,11,5],[12,3,11,7],[12,3,5,7],[12,11,5,7],[3,11,5,7],[12,3,11,5,7]
]
```
This video will help you get all possible combinations: https://www.youtube.com/watch?v=oXHJBHCXsnw

2) Filter those having a length less or equal than maxCities (3):

```js
[
[12],[3],[11],[5],[7],
[12,3],[12,11],[3,11],[12,5],[3,5],[11,5],[12,7],[3,7],[11,7],[5,7],
[12,3,11],[12,3,5],[12,11,5],[3,11,5],[12,3,7],[12,11,7],[3,11,7],[12,5,7],[3,5,7],[11,5,7]
]
```

3) Sum all elements in each sub-array:

```js
[12,3,11,5,7,15,23,14,17,8,16,19,10,18,12,26,20,28,19,22,30,21,24,15,23]
```

4) Filter those smaller than maxGifts (20):

```js
[20,19,19,18,17,16,15,15,14,12,12,11,10,8,7,5,3]
```

5) Return max of this array: `20`

### Readable iterative algorithm - Cognitive Complexity: 2 (~20 ops/s)

```js
function getMaxGifts(giftsCities, maxGifts, maxCities) {
  const getAllCombinations = (array) => {
    return new Array(1 << array.length)
      .fill()
      .map((e1, i) => array.filter((e2, j) => i & (1 << j)));
  };

  const allCombinations = getAllCombinations(giftsCities);

  const combinationsOfNOrLess = allCombinations
    .filter((combi) => combi.length <= maxCities && combi.length > 0);

  const combinationSums = combinationsOfNOrLess
    .map((combi) => {
      return combi.reduce((acc, weight) => acc + weight);
    });

  const validSumsSorted = combinationSums
    .filter((item) => item <= maxGifts)
    .sort((a, b) => b - a);

  const finalAmount = validSumsSorted[0] || 0;
  
  return finalAmount;
}

getMaxGifts([12, 3, 11, 5, 7], 20, 3); // 20
getMaxGifts([50], 15, 1); // 0
getMaxGifts([50], 100, 1); // 50
getMaxGifts([50, 70], 100, 1); // 70
getMaxGifts([50, 70, 30], 100, 2); // 100
getMaxGifts([50, 70, 30], 100, 3); // 100
getMaxGifts([50, 70, 30], 100, 4); // 100
```

### Recursive Algorithm (Backtrack) - Cognitive Complexity: 8 (~100 ops/s)

```js
function getMaxGifts(giftsCities, maxGifts, maxCities) { 
  const getGiftCount = (giftsCities, maxGifts, maxCities, i=0, giftCount=0, cityCount=0) => {
    if (cityCount === maxCities || i === giftsCities.length) {
      return giftCount;
    }
  
    if (giftCount + giftsCities[i] <= maxGifts) {
      return Math.max(
       getGiftCount(giftsCities, maxGifts, maxCities, i+1, giftCount+giftsCities[i], cityCount+1), 
       getGiftCount(giftsCities, maxGifts, maxCities, i+1, giftCount, cityCount)
      );
    }
  
    return getGiftCount(giftsCities, maxGifts, maxCities, i+1, giftCount, cityCount);
  }
  
  return getGiftCount(giftsCities, maxGifts, maxCities);
}

getMaxGifts([12, 3, 11, 5, 7], 20, 3); // 20
getMaxGifts([50], 15, 1); // 0
getMaxGifts([50], 100, 1); // 50
getMaxGifts([50, 70], 100, 1); // 70
getMaxGifts([50, 70, 30], 100, 2); // 100
getMaxGifts([50, 70, 30], 100, 3); // 100
getMaxGifts([50, 70, 30], 100, 4); // 100
```
