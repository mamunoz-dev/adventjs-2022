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

### 320 puntos (> 3000 ops/sec, Complejidad cognitiva: 2)

```js
function selectSleigh(distance, sleighs) {
  const battery = 20;
  
  const sleigh = sleighs
    .filter(sleigh => sleigh.consumption*distance <= battery)
    .pop();
  
  return sleigh && sleigh.name || null;
}
```

### 360 puntos (> 3000 ops/sec, Complejidad cognitiva: 1)

```js
function selectSleigh(distance, sleighs) {
  return sleighs
    .filter(sleigh => sleigh.consumption*distance <= 20)
    .map(sleigh => sleigh.name)
    .pop() || null;
}
```
