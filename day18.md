### 200 puntos

```js
function dryNumber(dry, numbers) {
  return Array.from(Array(numbers))
    .map((item, i) => i+1)
    .filter(item => item.toString().includes(dry));
}
```
