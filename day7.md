### 120 puntos

```js
function getGiftsToRefill(a1, a2, a3) {
  const uniqueGifts = [...new Set(a1.concat(a2).concat(a3))];
  
  return uniqueGifts.reduce((acc, gift) => {
    const existences = a1.some(g => g === gift) + a2.some(g => g === gift) + a3.some(g => g === gift);
    if(existences <= 1) acc.push(gift);
    return acc;
  }, []);
}
```

### 120 puntos

```js
function getGiftsToRefill(a1, a2, a3) {
  return [...new Set(a1.concat(a2).concat(a3))]
    .reduce((acc, gift) => {
      if (a1.some(g => g === gift) + a2.some(g => g === gift) + a3.some(g => g === gift) <= 1) {
        acc.push(gift);
      }
      return acc;
  }, []);
}
```

### 120 puntos

```js
function getGiftsToRefill(a1, a2, a3) {
  return [...new Set(a1.concat(a2).concat(a3))]
    .reduce((acc, gift) => {
      if (a1.includes(gift) + a2.includes(gift) + a3.includes(gift) <= 1) {
        acc.push(gift);
      }
      return acc;
  }, []);
}
```

### 200 puntos

```js
function getGiftsToRefill(a1, a2, a3) {
  return [...(new Set(a1.concat(a2,a3)))]
    .filter((gift) => a1.some(g => g === gift) + a2.some(g => g === gift) + a3.some(g => g === gift) === 1);
}
```

### 400 puntos

```js
function getGiftsToRefill(a1, a2, a3) {
  return [...(new Set(a1.concat(a2,a3)))]
    .filter((gift) => a1.includes(gift) + a2.includes(gift) + a3.includes(gift) == 1);
}
```