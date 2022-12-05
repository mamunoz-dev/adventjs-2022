### 99 points

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

  console.log(finalAmount);
  
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

### 123 points

```js
function getMaxGifts(giftsCities, maxGifts, maxCities) {
  const getAllCombinations = (array) => {
    return new Array(1 << array.length)
      .fill()
      .map((e1, i) => array.filter((e2, j) => i & (1 << j)));
  };

  const validSumsSorted = getAllCombinations(giftsCities)
    .filter((combi) => combi.length <= maxCities && combi.length > 0)
    .map((combi) => combi.reduce((acc, weight) => acc + weight))
    .filter((item) => item <= maxGifts);
  
  return validSumsSorted.length > 0 ?Math.max(...validSumsSorted) : 0;
}

getMaxGifts([12, 3, 11, 5, 7], 20, 3); // 20
getMaxGifts([50], 15, 1); // 0
getMaxGifts([50], 100, 1); // 50
getMaxGifts([50, 70], 100, 1); // 70
getMaxGifts([50, 70, 30], 100, 2); // 100
getMaxGifts([50, 70, 30], 100, 3); // 100
getMaxGifts([50, 70, 30], 100, 4); // 100
```

### 137 points

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
