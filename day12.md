### 220 puntos

```js
function selectSleigh(distance, sleighs) {
  const battery = 20;
  
  const sleigh = sleighs
    .map(sleigh => {
    return { name: sleigh.name, consumption: sleigh.consumption * distance }
  })
    .filter(sleigh => sleigh.consumption <= battery)
    .pop();
  
  return sleigh && sleigh.name || null;
}
```

### 320 puntos (> 3000 ops/sec)

```js
function selectSleigh(distance, sleighs) {
  const battery = 20;
  
  const sleigh = sleighs
    .filter(sleigh => sleigh.consumption*distance <= battery)
    .pop();
  
  return sleigh && sleigh.name || null;
}
```
