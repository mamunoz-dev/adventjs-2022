# Challenge #11: Santa Claus is Scrum Master

### Cognitive Complexity: 1 (>2000 ops/sec)

```js
function getCompleted(part, total) {
  const hms = [60 * 60, 60, 1];
  const getSeconds = (time) => 
    time
      .split(':')
      .map((val, i) => Number(val) * hms[i])
      .reduce((acc, val) => acc + val, 0);
  
  const [partSeconds, totalSeconds] = [part, total].map(getSeconds);
  let [numerator, denominator] = [partSeconds, totalSeconds];
  
  while(denominator !== 0) {
    [denominator, numerator] = [numerator % denominator, denominator];
  }
  
  return `${partSeconds/numerator}/${totalSeconds/numerator}`;
}
```
