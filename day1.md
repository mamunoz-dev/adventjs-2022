### 132 points

```js
wrapping = (gifts) => gifts.map(gift => {
  const sideWrap = '*'.repeat(gift.length+2);
  return `${sideWrap}\n*${gift}*\n${sideWrap}`;
});
```
