# Challenge #17: Carrying gifts in bags

### Cognitive Complexity: 3 (>2000 ops/s)

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
