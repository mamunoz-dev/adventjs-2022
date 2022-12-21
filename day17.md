### 100 puntos (>2000 ops/sec, Complejidad cognitiva: 5)

```js
function carryGifts(gifts, maxWeight) {
  return gifts.reduce((acc, curr) => {
    if (!acc[acc.length-1]) {
      acc[acc.length-1] = [];
    }
    
    if((acc[acc.length-1].join('').length + curr.length) <= maxWeight) {
      acc[acc.length-1].push(curr)
    } else if (curr.length <= maxWeight) {
      acc = [...acc, [curr]];
    }
    
    return acc;
  }, [[]])
  .map(elm => elm.join(' '))
  .filter(elm => elm);
}
```

### 180 puntos (>2000 ops/sec, Complejidad Cognitiva 3)

```js
function carryGifts(gifts, maxWeight) {
  return gifts
    .reduce(
      (prev, curr) => {
        const gift = prev[0].replace(/ /g, "");
        if (curr.length + gift.length <= maxWeight) {
          prev[0] += ` ${curr}`;
          prev[0] = prev[0].trim();
          return prev;
        }
        else if (curr.length <= maxWeight) {
          prev.unshift(curr);
        }
        return prev;
      },
      [""]
    )
    .reverse()
    .filter((el) => el);
```
