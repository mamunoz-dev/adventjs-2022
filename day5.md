### Algoritmo iterativo (hasta 170 puntos)

Suponiendo los siguientes inputs:

```js
const giftsCities = [12, 3, 11, 5, 7]
const maxGifts = 20
const maxCities = 3
```

1) Sacar todas las posibles combinaciones de elementos del array:

```js
[
[12],[3],[11],[5],[7],
[12,3],[12,11],[3,11],[12,5],[3,5],[11,5],[12,7],[3,7],[11,7],[5,7],
[12,3,11],[12,3,5],[12,11,5],[3,11,5],[12,3,7],[12,11,7],[3,11,7],[12,5,7],[3,5,7],[11,5,7],
[12,3,11,5],[12,3,11,7],[12,3,5,7],[12,11,5,7],[3,11,5,7],[12,3,11,5,7]
]
```
Este vídeo puede ayudarte a sacar todas laa combinaciones: https://www.youtube.com/watch?v=oXHJBHCXsnw

2) Filtrar las que tengan un tamaño igual o menor que maxCities (3):

```js
[
[12],[3],[11],[5],[7],
[12,3],[12,11],[3,11],[12,5],[3,5],[11,5],[12,7],[3,7],[11,7],[5,7],
[12,3,11],[12,3,5],[12,11,5],[3,11,5],[12,3,7],[12,11,7],[3,11,7],[12,5,7],[3,5,7],[11,5,7]
]
```

3) Hacer la suma de los elementos de cada sub-array:

```js
[12,3,11,5,7,15,23,14,17,8,16,19,10,18,12,26,20,28,19,22,30,21,24,15,23]
```

4) Filtrar aquellos que sean menores que maxGifts (20):

```js
[20,19,19,18,17,16,15,15,14,12,12,11,10,8,7,5,3]
```

5) Devolver el máximo de ese array: `20`

### Algoritmo Recursivo

Próximamente...

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
