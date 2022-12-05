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
