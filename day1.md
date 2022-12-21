# Challenge #1: Automating Christmas gift wrapping!

### Cognitive Complexity: 1 (>2000 ops/s)

```js
function wrapping(gifts) {
  return gifts.map(gift => {
    const sideWrap = '*'.repeat(gift.length+2);
    return `${sideWrap}\n*${gift}*\n${sideWrap}`;
  });
}
```
