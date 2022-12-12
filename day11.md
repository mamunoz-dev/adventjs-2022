### 220 points

```js
function getCompleted(part, total) {
  const getTimeArray = (time) => time.split(':').map(elm => Number(elm));
  const mcd = (a, b) => {
    let temporal;
    while (b !== 0) {
        temporal = b;
        b = a % b;
        a = temporal;
    }
    return a;
  };
  
  const p = getTimeArray(part);
  const t = getTimeArray(total);
  
  const dateRef = new Date(0);
  const num = dateRef.setHours(p[0], p[1], p[2]) / 1000;
  const den = dateRef.setHours(t[0], t[1], t[2]) / 1000;

  const divider = mcd(num, den);
  
  return `${num/divider}/${den/divider}`;
}
```

### 260 or 160 points (> 2000 ops/sec or < 2000 ops/sec)

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
